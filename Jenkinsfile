pipeline {
    agent any

    stages {
        stage('Pull Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Abhinandan-58/Jarvis-Desktop-Voice-Assistant.git'
            }
        }

        stage('Deploy to EC2') {
            steps {
                sh '''
                ssh -o StrictHostKeyChecking=no ubuntu@34.213.232.253 "
                  cd /home/ubuntu/Jarvis-Desktop-Voice-Assistant &&
                  git pull &&
                  pip3 install -r requirements.txt &&
                  sudo systemctl restart jarvis
                "
                '''
            }
        }
    }
}