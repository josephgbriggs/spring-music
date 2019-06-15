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
		sh 'gradle wrapper --gradle-version=5.1.1 assemble'
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