pipeline {
	agent {
		label 'Docker'
	}
	stages {
		stage ("Making Required Server Up") {
			steps {
				sh 'docker-compose up -d hub chrome firefox'
			}
		}
		stage ("Running Test cases") {
			steps {
				sh 'docker-compose up testng'
			}
		}
	}
	post {
		always {
			archiveArtifacts artifacts:'result/**'
			sh 'docker-compose down'
		}
	}
}	