pipeline {
	agent any
	environment {
    NVD_API_KEY = credentials('nvdkey')
  }
	stages {
		stage('Checkout SCM') {
			steps {
				checkout scm
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP-Dependency-Check'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}