pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				checkout scm
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML --suppression suppression.xml', odcInstallation: 'OWASP_Dependency-Check_Vulnerabilities'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}