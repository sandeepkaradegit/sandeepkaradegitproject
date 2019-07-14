pipeline {
	environment {
		JOB_NAME = "${env.JOB_NAME}"
	        BUILD_NUMBER = "${env.BUILD_NUMBER}"
	    	}
	agent {
        	label 'DOCKERNEW'
	       	}
	stages {
	    stage('Job123PREPARE') {
	      	steps {
	            	sh 'java -version'
	            	echo 'Puppet Agent Install and Configure..'
			sh 'sudo apt-get update'
			sh 'sudo apt-get install puppet -y'
			sh 'sudo sh -c "echo [agent] >> /etc/puppet/puppet.conf"'
		 	sh 'sudo sh -c "echo server=ip-172-31-35-33.eu-central-1.compute.internal >> /etc/puppet/puppet.conf"'              
			sh 'sudo puppet agent --enable'
			echo 'Puppet Agent will install Docker and Git CLI..'
			sh 'sudo puppet agent -t|| true'
			sh 'git --version'
			sh 'docker --version'
			sh 'mkdir /home/ubuntu/jenkin-agent|| true'
		       }
	        }
	    stage('Job4BUILD')   {
	       	steps {
	               	echo 'Docker image build started..'
	   		sh 'sudo docker images'
			sh 'sudo docker ps -a'
			sh 'sudo docker pull php:apache'
			sh 'sudo docker stop ${JOB_NAME}${BUILD_NUMBER}||true'
			sh 'sudo docker rm ${JOB_NAME}${BUILD_NUMBER}||true'
			sh 'sudo docker run -d --name=${JOB_NAME}${BUILD_NUMBER} -p 80${BUILD_NUMBER}:80 -v /home/ubuntu/jenkin-agent/workspace/devops/website:/var/www/html php:apache'
			sh 'sudo docker images'
			sh 'sudo docker ps -a'
			echo 'Docker image build started..'
	            }
	        }
	    stage('Job4TEST') {
	        steps {
	                echo 'Testing..'
	            }
	        }
	 }
	    post {
	        always {
	            sh 'exit 0'
	               }
                 }
}
