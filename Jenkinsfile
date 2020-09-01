pipeline {
    agent any
    
    tools {
        maven 'maven3'
    }
    
    stages {
        stage('Install') {
            steps {
                sh "mvn clean test"
            }
            post {
                always {
                    junit '**/target/*-reports/TEST-*.xml'
                }
            }
        }
            stage('Sonar') {
                steps {
                    sh "mvn sonar:sonar -Dsonar.host.url=${"http://sonarqube:9000"}"
            }
        }
    }
}
