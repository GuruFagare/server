pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                // Add your build commands here if needed
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add your test commands here if needed
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Example: Copy the `Index.html` file to a deployment directory
                sh 'cp Index.html ubuntu@15.207.221.231:/var/www/html'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
