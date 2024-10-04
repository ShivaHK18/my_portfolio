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

    stage('Compile') {
      steps {
        sh 'mvn clean compile'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn clean test'
      }
    }

    stage('Sonar Analysis') {
      steps {
        sh '''mvn sonar:sonar \
        -Dsonar.host.url=http://35.154.147.215:9000/ \
        -Dsonar.login=squ_d37e5dca65cb48d05f12080a8221779afa7755f0 \
        -Dsonar.projectName=portfolio \
        -Dsonar.java.binaries=. \
        -Dsonar.projectKey=portfolio '''
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
  }
}
