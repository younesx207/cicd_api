pipeline {
    agent any
    
    environment {
        MULE_HOME = 'C:\7.15\AnypointStudio-7.15.0-win64\AnypointStudio\plugins\org.mule.tooling.server.4.4.0.ee_7.11.0.202303211414\mule'
        MULE_PROJECT_NAME = 'cicd_exercise'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Check out your MuleSoft project from version control
                    checkout scm
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build the MuleSoft project using Maven or any other build tool
                    sh "${MULE_HOME}/bin/mule -e ${MULE_PROJECT_NAME} clean package"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run tests for your MuleSoft project
                    sh "${MULE_HOME}/bin/mule -e ${MULE_PROJECT_NAME} test"
                }
            }
        }

    }

    post {
        success {
            echo 'MuleSoft project successfully built, tested, and deployed!'
        }

        failure {
            echo 'MuleSoft project build, test, or deployment failed.'
        }
    }
}