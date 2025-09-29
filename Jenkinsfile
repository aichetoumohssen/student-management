pipeline {
    agent any  // Exécute sur n’importe quel agent Jenkins disponible

    tools {
        maven 'Maven'     // Nom configuré dans "Manage Jenkins > Global Tool Configuration"
        jdk 'jdk17'       // Nom de ton JDK configuré
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/aichetoumohssen/student-management.git'
            }
        }

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

        stage('Package') {
            steps {
                sh 'mvn package'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
                }
            }
        }
    }
}
