pipeline {
    agent any

    tools {
        jdk 'jdk8'
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
            stage('Sonar') {
            steps {
                sh "mvn sonar:sonar -Dsonar.host.url=${"http://sonar:9000"}"
            }
        }
    }
}
