pipeline {
  agent any
  tools {
    maven 'maven'
  }
  environment {
    SONAR_HOST_URL = 'http://host.docker.internal:9000' // URL de SonarQube
    SONAR_LOGIN = 'squ_54097c4885369a632457d1654be7cbbbda012cef'  // Token d'authentification
  }
  stages {
    stage('Build & Analyse avec SonarQube') {
      steps {
        script {
          sh 'mvn clean package sonar:sonar -Dsonar.host.url=$SONAR_HOST_URL -Dsonar.login=$SONAR_LOGIN'
        }
      }
    }
  }
}
