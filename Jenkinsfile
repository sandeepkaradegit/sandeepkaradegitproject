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
		sh 'sudo docker pull php:apache'
		sh 'docker run -d --name=apachetest -p 8085:80 -v /home/ubuntu/jenkin-agent/workspace/devops/website:/var/www/html php:apache'
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
