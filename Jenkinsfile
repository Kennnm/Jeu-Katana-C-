pipeline {
  agent any
  tools {
    maven 'maven'  // Assurez-vous que 'maven' est bien configuré dans Global Tool Configuration
  }
  environment {
    SONAR_HOST_URL = 'http://host.docker.internal:9000'  // URL de SonarQube
    SONAR_LOGIN = 'squ_54097c4885369a632457d1654be7cbbbda012cef'  // Token d'authentification
  }
  stages {
    stage('Vérification Maven') {
      steps {
        script {
          // Vérifie si Maven est installé et accessible
          sh 'mvn -version'
        }
      }
    }
    stage('Build & Analyse avec SonarQube') {
      steps {
        script {
          // Exécute le build Maven et analyse avec SonarQube
          sh 'mvn clean package sonar:sonar -Dsonar.host.url=$SONAR_HOST_URL -Dsonar.login=$SONAR_LOGIN'
        }
      }
    }
    stage("deploy & OWASP Dependency-Check") {
      steps {
          dependencyCheck additionalArguments: '''
              -o './'
              -s './'
              -f 'ALL'
              --prettyPrint''',
              odcInstallation: 'owasp-dependency'
          
          dependencyCheckPublisher pattern: 'dependency-check-report.html'
      }
    }  
  }
}
