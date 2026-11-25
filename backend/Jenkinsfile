pipeline {
    agent any
    environment { MAVEN_OPTS = '-Djava.net.preferIPv4Stack=true' }
    stages {
        stage('Checkout') { steps { checkout scm } }
        stage('Build Backend') {
            steps { dir('backend') { sh 'mvn clean package -DskipTests' } }
        }
        stage('Archive') {
            steps { archiveArtifacts artifacts: 'backend/target/*.jar', fingerprint: true }
        }
    }
}
