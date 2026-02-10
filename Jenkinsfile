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
            }
        }
    }
}
