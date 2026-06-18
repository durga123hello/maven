pipeline {
    agent any
    stages {
        stage('Checkout') {
            sed -i "s|git 'https://github.com/durga123hello/maven.git'|git branch: 'main', url: 'https://github.com/durga123hello/maven.git'|" Jenkinsfile
        }
        stage('Build') {
            steps { sh 'mvn clean package' }
        }
        stage('Test') {
            steps { sh 'mvn test' }
        }
    }
    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }
        success {
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
    }
}
