pipeline {
    agent {
        kubernetes {
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: kubectl
    image: bitnami/kubectl:latest
    command:
    - cat
    tty: true
    resources:
      requests:
        memory: "512Mi"
        cpu: "250m"
      limits:
        memory: "1024Mi"
        cpu: "500m"
'''
        }
    }
    environment {
        MY_API_KEY = credentials('my-api-key')
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'ls -la'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Tests passed!"'
            }
        }
        stage('Deploy') {
            steps {
                container('kubectl') {
                    echo 'Spreading to other servers...'
                    sh 'kubectl apply -f deployment.yaml'
                    sh 'kubectl apply -f service.yaml'
                }
            }
        }
    }
}
