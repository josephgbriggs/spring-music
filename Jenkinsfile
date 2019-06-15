pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
		  echo 'Cloning...'
        git(url: 'https://github.com/josephgbriggs/spring-music.git', branch: 'master')
      }
    }
	stage('Build') {
	  steps {
	    echo 'Building...'
		if (isUnix()) {
		  sh './gradlew assemble'
		} else {
		  bat 'gradlew.bat assemble'
		}
	  }
	}
	stage('Test') {
	  steps {
	    echo 'Testing...'
	  }
	}
	stage('Deploy') {
	  steps {
		  pushToCloudFoundry(
		    target: 'https://api.dev.cfdev.sh',
		    organization: 'cfdev-org',
		    cloudSpace: 'cfdev-space',
		    credentialsId: 'cf-api-user',
			selfSigned: 'true'
		  )
	  }
	}
  }
}