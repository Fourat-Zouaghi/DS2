pipeline {
    agent any
    stages {
        stage('Checkout Git') {
            steps {
                git branch: 'main', url: 'https://github.com/Fourat-Zouaghi/DS2.git'
            }
        }
        stage('Build Maven') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Analyse SonarQube') {
            steps {
                withSonarQubeEnv('SonarQube-Server') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("school-app:latest")
                }
            }
        }
    }
}