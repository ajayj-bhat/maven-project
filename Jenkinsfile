
pipeline {
    agent any
    stages{
        stage('Build'){
            tools{
                maven 'localMaven'
            }
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}