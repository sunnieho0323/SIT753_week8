pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "/my/code/path"
        TESTING_ENVIRONMENT = "Testing"
        PRODUCTION_ENVIRONMENT = "SunnieHo"
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from the directory path specified by the environment variable"
                echo "Compile the code and generate any necessary artefacts"
            }
        }

        stage('Test') {
            steps {
                echo "Unit tests"
                echo "Integration tests"
            }
        }

        stage('Code Quality Check') {
            steps {
                echo "Check the quality of the code"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploy the application to a testing environment specified by the environment variable"
            }
        }

        stage('Approval') {
            steps {
                sleep 10
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploy the code to the production environment: ${env.PRODUCTION_ENVIRONMENT}"
            }
            post {
                always {
                    emailext(
                        to: 'sunnieho790323@gmail.com',
                        subject: "Testing Deployment Notification: ${env.PRODUCTION_ENVIRONMENT}",
                        body: "The application has been deployed to the production environment: ${env.PRODUCTION_ENVIRONMENT}",
                        attachBuildLog: true,
                        compressBuildLog: true
                    )
                }
            }
        }
    }
}