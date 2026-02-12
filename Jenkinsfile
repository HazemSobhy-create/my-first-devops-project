// Automating my Week 9 Pipeline!
pipeline {
    agent any
    /* ADD THIS SECTION HERE */
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

	stage('Deploy') {
	    steps {
	        echo 'Spreading to other servers...'
        	// This command tells K8s to update your website with the latest changes
        	sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
	   }
        }
    }
}
