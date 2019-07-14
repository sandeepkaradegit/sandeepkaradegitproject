pipeline {
    agent any
    stages {
        stage('one') {
            steps {
		echo 'one'
                sh 'exit 0'
            }
        }
        stage('two') {
            steps {
		echo 'two'
                sh 'exit 1'   // failure
            }
        }
	stage('three') {
            steps {
		echo 'three'
                sh 'exit 0'   // failure
            }
        }
    }
    post {
        always {
	    echo 'post'
            sh 'exit 0'
        }
    }
}
