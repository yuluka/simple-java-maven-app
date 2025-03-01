pipeline {
    agent any
    stages {
        stage('Cleanup') {
            steps {
                bat '''
                if exist "simple-java-maven-app" (
                    echo La carpeta existe, eliminándola...
                    rmdir /s /q simple-java-maven-app
                ) else (
                    echo La carpeta NO existe, continuando...
                )
                '''
            }
        }
        stage('Checkout') {
            steps {
                git 'https://github.com/jenkins-docs/simple-java-maven-app.git'
            }
        }
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
    }
}
