pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Zip build'
                sh 'zip -r "build-$(date +"%Y-%m-%d-%h-%m-%s").zip" .'
            }
        }
        stage('Test') {
            steps {
                echo 'SHOW Path'
                sh 'pwd'
            }
        }
        stage('Deploy') {
            steps {
                echo 'COPY FILE TO REMOTE HOST & Depoy Build'
                sh 'scp -r "build-$(date +"%Y-%m-%d-%h-%m-%s").zip" kundan@server1:/tmp/'
                sh 'ssh kundan@server1 sudo unzip -o -d /var/www/hello/ /tmp/build-$(date +"%Y-%m-%d-%h-%m-%s").zip'

            }
        }
    }
}

