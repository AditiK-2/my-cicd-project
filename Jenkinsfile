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

	 	sshagent(['app-ec2-key-3']) {
            sh '''
                scp -o StrictHostKeyChecking=no index.html ubuntu@13.51.204.120:/tmp/index.html
                ssh -o StrictHostKeyChecking=no ubuntu@13.51.204.120 "sudo cp /tmp/index.html /var/www/html/index.html"
            '''
               }
            }
        }
    }
}
