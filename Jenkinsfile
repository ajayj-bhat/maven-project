
pipeline {
    agent any
    stages{
        stage('Build'){
            tools{
                maven 'apache-maven-3.5.3'
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