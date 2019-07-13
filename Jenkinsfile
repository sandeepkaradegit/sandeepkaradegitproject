pipeline {
    agent {
        label 'PHPonDocker'
        }

    stages {
    	  stage('Get') {
            steps {
                git 'https://github.com/sandeepkaradegit/sandeepkaradegitproject.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Git Auto trigger Building..'
		sh 'sudo docker ps'
                sh 'sudo docker build -t mysite /home/ubuntu/jenkin-agent/workspace/devops/'
		sh 'sudo docker run -p 8080:80 -d mysite'
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
            }
        }
    }
}
