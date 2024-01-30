pipeline {
    agent any

    tools {
        // Define the Maven tool used for the build
        maven 'Maven3'
    }

    stages {
        stage('Checkout') {
            steps {
                // Check out the MuleSoft project from version control
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build the MuleSoft project using Maven
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                // Run tests for the MuleSoft project using Maven
                sh 'mvn test'
            }
        }
    }

    post {
        success {
            echo 'MuleSoft project successfully built and tested!'
        }

        failure {
            echo 'MuleSoft project build or test failed.'
        }
    }
}