pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Copy all site files to remote Nginx server
                sh 'scp -r * ubuntu@15.207.221.231:/var/www/html'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
