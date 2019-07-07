pipeline {
    agent {
        node {
            label 'PHPonDocker'
            customWorkspace '/home/ubuntu/jenkin-agent'
            }
         }

    stages {
        stage('Get') {
            steps {
                sudo apt-get update
                sudo apt-get install git
                git 'https://github.com/sandeepkaradegit/sandeepkaradegitproject.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Git Auto trigger Building..'
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
