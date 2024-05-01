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
                echo 'JUnit test for code function.'
                echo 'Integration Test working together.'
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
                 echo 'Performing code analysis using SonarQube'
            }
        }

        stage("Security Scan") {
            steps {
               echo 'Performing security scan using SonarQube'
            }
             post{ 
                    always{
                        eamiltext attachLog: true, subject: "Security Scan Status: ${currentBuild.result}",
                        body: "The security scan stage has completed. Status: ${currentBuild.result}",
                        to: "justincuber7@gmail.com"
                    }
                }
        }

        stage("Deploy to Staging") {
            steps {
                 echo 'Deploy to staging sever AWS EC2 s3://staging-bucket/'
            }
        }

        stage("Integration Tests on Staging") {
            steps {
                echo 'Run Integration Tests on Staging environment'
                sleep 10
            }
        }

        stage("Deploy to Production") {
            steps {
                echo'Deploy to Production server AWS EC2'
            }
            
        }
    }
}
