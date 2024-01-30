pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the MuleSoft project from version control
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build the MuleSoft project using the default Maven tool
                script {
                    def mavenHome = tool 'Maven'
                    sh "${mavenHome}/bin/mvn clean package"
                }
            }
        }

        stage('Test') {
            steps {
                // Run tests for the MuleSoft project using the default Maven tool
                script {
                    def mavenHome = tool 'Maven'
                    sh "${mavenHome}/bin/mvn test"
                }
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