pipeline {
    agent any

    
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
