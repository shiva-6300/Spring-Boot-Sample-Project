pipeline {
    agent any

    tools {
        maven 'Maven3'   // Must match Global Tool Configuration
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/shiva-6300/Spring-Boot-Sample-Project.git'
            }
        }

        stage('Clean & Build') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'mvn test'
            }
        }
    }

    post {
        success {
            echo 'Build & Tests Successful'
        }
        failure {
            echo 'Build or Tests Failed'
        }
    }
}
