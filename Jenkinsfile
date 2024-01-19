pipeline {
    agent any
    tools {
        maven 'Maven 3.8.6'
        jdk 'Java 17.0.4.1'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
    post {
        always {
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
        }
    }
}
