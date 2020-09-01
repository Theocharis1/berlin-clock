pipeline {
    agent any
    
    tools {
        jdk 'openjdk-11'
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
