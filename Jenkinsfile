pipeline {
    agent any
    
    env.JAVA_HOME = tool 'jdk14'
    
    tools {
        jdk 'jdk14'
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
