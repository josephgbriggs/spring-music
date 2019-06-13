pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/josephgbriggs/spring-music.git', branch: 'master')
      }
    }
  }
}