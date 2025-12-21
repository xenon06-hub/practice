pipeline {
    agent any

    stages {

        stage('Verify Files') {
            steps {
                echo 'Listing project files...'
                sh 'ls -la'
            }
        }

        stage('Deploy to Nginx') {
            steps {
                echo 'Deploying HTML to Nginx (port 80)...'
                sh '''
                sudo rm -rf /var/www/html/*
                sudo cp *.html /var/www/html/
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment successful! Website live on port 80.'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
