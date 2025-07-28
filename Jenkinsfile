pipeline {
    agent any

    environment {
        // Optional: define any global env variables
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Gauravgk12/Mywebsite/', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
