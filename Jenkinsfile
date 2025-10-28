pipeline {
    agent any

    stages {
        stage('Pull from GitHub') {
            steps {
                echo 'Cloning the latest code...'
                git branch: 'main', url: 'https://github.com/<your-username>/apache-web-deploy.git'
            }
        }

        stage('Deploy to Apache') {
            steps {
                echo 'Deploying files to Apache web server...'
                sh '''
                    sudo rm -rf /var/www/html/*
                    sudo cp -r * /var/www/html/
                    sudo systemctl restart httpd
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Deployment Successful!'
        }
        failure {
            echo '❌ Deployment Failed!'
        }
    }
}
