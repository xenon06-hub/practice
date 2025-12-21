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
           sh '''
           sudo rm -rf /var/www/html/*
           sudo cp *.html *.css /var/www/html/
           sudo chown -R www-data:www-data /var/www/html
           sudo chmod -R 755 /var/www/html
           sudo systemctl reload nginx
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
