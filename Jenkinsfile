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
                echo 'Docker image build started..'
		sh 'sudo docker ps'
                sh 'sudo docker build -t phpapacheimage /home/ubuntu/jenkin-agent/workspace/devops/'
		sh 'docker run -d --name=apachetest -p 8083:80 -v /home/ubuntu/jenkin-agent/workspace/devops/website:/var/www/html php:apache'
		echo 'Docker image build started..'
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
