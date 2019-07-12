pipeline {
    agent {
        node {
            label 'PHPonDocker'
            }
         }

    stages {
        stage('Get') {
            steps {
                git 'https://github.com/sandeepkaradegit/sandeepkaradegitproject.git'
                cd /home/ubuntu/jenkin-agent/workspace/devops
            }
        }
        stage('Build') {
            steps {
                echo 'Git Auto trigger Building..'
                docker build -t mysite /home/ubuntu/jenkin-agent/workspace/devops
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                docker run -p 8080:80 -d mysite
            }
        }
    }
}
