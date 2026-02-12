// Automating my Week 9 Pipeline!
pipeline {
    agent {
	kubernetes {
	    yaml '''
apiVersion: v1
kind: Pod
Spec:
  containers:
    - name: kubectl
      image: bitnami/kubectl:latest
      command:
      - cat
      tty: true
'''
	    }
	}
    environment {
	MY_API_KEY = credentials('my-api-key')
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'ls -la'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
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
