pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git(url: 'https://github.com/josephgbriggs/spring-music.git', branch: 'master')
      }
    }
	stage('Build') {
	  steps {
	    echo 'Building..'
	  }
	}
	stage('Test') {
	  steps {
	    echo 'Testing..'
	  }
	}
	stage('Deploy') {
	  steps {
		  pushToCloudFoundry(
		    target: 'https://apps.dev.cfdev.sh/',
		    organization: 'cfdev-org',
		    cloudSpace: 'cfdev-space',
		    credentialsId: 'cf-api-user',
			selfSigned: 'true'
		  )
	  }
	}
  }
}