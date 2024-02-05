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
        		script {
            	// Specify the full path to the Maven executable
            	def mavenHome = tool 'Maven 3.8'
            	def mavenExecutable = "${mavenHome}/bin/mvn"

            	echo "Maven home: ${mavenHome}"
            	echo "Maven executable: ${mavenExecutable}"

            	// Print the Maven version
            	bat "${mavenExecutable} --version"

            	// Build the MuleSoft project using Maven
            	bat "${mavenExecutable} clean package -nsu -DskipMunitTests"
        	}
    		}
		}

        stage('Test') {
            steps {
                // Run tests for the MuleSoft project using the default Maven tool
                script {
                    def mavenHome = tool 'Maven 3.8'
            		def mavenExecutable = "${mavenHome}/bin/mvn"
            		
            		bat "${mavenExecutable} clean package -nsu -DskipMunitTests"
                }
            }
        }
    }
    
    	stage('Deploying to cloudhub') {
            steps {
                script {
                    def mavenHome = tool 'Maven 3.8'
            		def mavenExecutable = "${mavenHome}/bin/mvn"
            		
            		bat "${mavenExecutable} clean deploy -DmuleDeploy -Dmule.version=4.4.0 -Dusername=YounesCap4 -Dpassword=CicdExercise1 -Denv=Sandbox -Dappname=cicd-exercise -Dbusiness=cap -DvCore=Micro -Dworkers=1"
                }
            }
        }
    }

    post {
        success {
            echo 'MuleSoft project successfully built, tested and deployed!'
        }

        failure {
            echo 'MuleSoft project build, test or deploy failed.'
        }
    }
}