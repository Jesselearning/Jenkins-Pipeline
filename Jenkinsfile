pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                echo  'Building project to compile and package using Maven.'
            }
        }

        stage("Unit and Integration Tests") {
            steps {
                echo 'Running unit and integration tests...'
                echo 'Using pytest...'      
            }
            post{ 
                    always{
                        eamiltext attachLog: true, subject: "Test Status: ${currentBuild.result}",
                        body: "Test Stage COMPLETE. Status: ${currentBuild.result}",
                        to: "justincuber7@gmail.com"
                    }
                }
        }

        stage("Code Analysis") {
            steps {
                echo "Check the quality of the code"
                echo 'Integrate SonarQube for code analysis'
            }
        }

        stage("Security Scan") {
            steps {
               echo 'Performing security scan using SonarQube'
            }
             post{ 
                    always{
                        emailext attachLog: true, subject: "Security Scan Status: ${currentBuild.result}", 
                        body: "The security scan stage has completed. Status: ${currentBuild.result}",
                        to: "justincuber7@gmail.com"
                    }
                }
        }

        stage("Deploy to Staging") {
            steps {
                echo "Deploy application to a staging server"
                echo "AWS using Jenkins."
            }
        }

        stage("Integration Tests on Staging") {
            steps {
                echo "Run integration tests on the staging environment to ensure the application functions as expected in a production-like environment"
                sleep 10
            }
        }

        stage("Deploy to Production") {
            steps {
                echo "Product is complete"
                echo "AWS server using Jenkins"
            } 
        }
    }
}
