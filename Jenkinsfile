
pipeline {
    agent any
    stages{
        stage('Build'){
            tools{
                maven 'localMaven'
            }
            steps {
                bat 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy-To-Staging'){
            steps {
                build job: 'deploy-to-staging'
            }
        }
        stage('Deploy-To-Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }

                build job: 'deploy-to-prod'
            }
            post{
                success{
                    echo 'Code Deployed to Production.'
                }
                failure{
                    echo 'Deployment failed.'
                }
            }
        }
    }
}