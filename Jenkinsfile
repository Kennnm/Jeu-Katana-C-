pipeline {
  agent none
  stages {
    stages("Build & Analyse avec SonarQube") {
      agent any
      steps {
        script {
          sh 'mvn clean package sonar:sonar'
        }
      }
    }
  }
}
