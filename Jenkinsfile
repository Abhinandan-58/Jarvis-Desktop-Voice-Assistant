pipeline {
    agent any

    environment {
        KEY = credentials('ec2-key')   // Jenkins credentials ID
    }

    stages {
        stage('Pull Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Abhinandan-58/Jarvis-Desktop-Voice-Assistant.git'
            }
        }

        stage('Deploy to EC2') {
            steps {
                sh '''
                ssh -o StrictHostKeyChecking=no -i jarvis-key ubuntu@54.187.86.180 << EOF
                  cd /home/ubuntu/Jarvis-Desktop-Voice-Assistant
                  sudo git pull
                  sudo pip3 install -r requirements.txt
                  sudo systemctl restart jarvis
                EOF
                '''
            }
        }
    }
}