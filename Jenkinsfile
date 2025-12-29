pipeline {
    agent any

    tools {
        maven 'Maven3'
    }

    environment {
        MAVEN_OPTS = "--add-opens jdk.compiler/com.sun.tools.javac.processing=ALL-UNNAMED"
    }

    stages {

        stage('Verify Java') {
            steps {
                bat 'java -version'
                bat 'mvn -version'
            }
        }

        stage('Checkout Code') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/shiva-6300/Spring-Boot-Sample-Project.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
    }

    post {
        success {
            echo 'BUILD SUCCESSFUL'
        }
        failure {
            echo 'BUILD FAILED'
        }
    }
}
