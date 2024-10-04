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
        -Dsonar.host.url=
        -Dsonar.login=
        -Dsonar.projectName=portfolio \
        -Dsonar.java.binaries=. \
        -Dsonar.projectKey=portfolio '''
      }
    }
  }
}
