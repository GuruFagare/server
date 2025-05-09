pipeline {
    agent any

    environment {
        REMOTE_USER = 'ubuntu'
        REMOTE_HOST = '15.206.194.169'
        REMOTE_PATH = '/var/www/html'
        REPO_URL = 'https://github.com/GuruFagare/Jenkins.git'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out main branch...'
                git branch: 'main', url: "https://github.com/GuruFagare/Jenkins.git"
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'

                // If using SSH credentials stored in Jenkins:
                // Replace 'your-ssh-credentials-id' with the actual ID from Jenkins credentials
                sshagent(credentials: ['SHA256:n7KfvCkb78APHSfJ1lT7FbaiMiPcv7HJArK0YuL7T9Y']) {
                    sh """
                        echo 'Copying files to remote server...'
                        scp -o StrictHostKeyChecking=no -r * ubuntu@15.206.194.169:/var/www/html

                    """
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
    }
}
