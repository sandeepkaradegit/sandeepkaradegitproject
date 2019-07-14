pipeline {
    agent {
        label 'DOCKERNEW'
        }

    stages {
    	  stage('Preparation') {
            steps {
            		sh 'java -version'
            		echo 'Puppet Agent Install and Configure..'
			sh 'sudo apt-get update'
			sh 'sudo apt-get install puppet -y'
			sh 'sudo sh -c "echo [agent] >> /etc/puppet/puppet.conf"'
		        sh 'sudo sh -c "echo server=ip-172-31-35-33.eu-central-1.compute.internal >> /etc/puppet/puppet.conf"'
			sh 'sudo puppet agent --enable'
			echo 'Puppet Agent will install Docker and Git CLI..'
			sh 'sudo puppet agent -t'
			sh 'git --version'
			sh 'docker --version'
		    	sh 'mkdir /home/ubuntu/jenkin-agent'
		    	catchError {
            build job: 'system-check-flow'
        		}
        		echo currentBuild.result
            }
        }
        
    	/*  stage('GetSource') {
            steps {
                git 'https://github.com/sandeepkaradegit/sandeepkaradegitproject.git'
            }
        }*/
        stage('Build') {
            steps {
                echo 'Docker image build started..'
		sh 'sudo docker pull php:apache'
		sh 'sudo docker run -d --name=apachetest -p 8085:80 -v /home/ubuntu/jenkin-agent/workspace/devops/website:/var/www/html php:apache'
		sh 'sudo docker images'
		sh 'sudo docker ps -a'
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
