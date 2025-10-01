pipeline {
    agent any
    tools {
        maven 'Maven'   // Doit correspondre au nom configuré dans Jenkins
        jdk 'jdk17'     // Idem pour le JDK configuré dans Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aichetoumohssen/student-management.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {  // "sonarqube" = nom de ton serveur dans Jenkins
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}

