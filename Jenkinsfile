pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting source code...'
                git branch: 'main',
                    url: 'https://github.com/AditiK-2/my-cicd-project.git'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'test -f index.html'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'mkdir -p build'
                sh 'cp index.html build/'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }
}