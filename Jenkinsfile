pipeline {
  agent any

  tools {
    jdk 'jdk11'
    maven 'maven3'
  }

  environment {
    SCANNER_HOME = tool 'sonar-scanner'
  }

  stages {
    stage('Git Checkout') {
      steps {
        git branch: 'main', changelog: false, poll: false, url: 'https://github.com/ShivaHK18/my_portfolio.git'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('Sonar Analysis') {
      steps {
        sh '''mvn sonar:sonar \
        -Dsonar.host.url=http://13.235.242.184:9000/ \
        -Dsonar.login=squ_0f880b8ca8f3a288e8ae2249eab904c5f055e032 \
        -Dsonar.projectName=portfolio \
        -Dsonar.java.binaries=. \
        -Dsonar.projectKey=portfolio '''
      }
    }
  }
}
