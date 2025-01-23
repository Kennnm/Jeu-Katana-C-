pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage("build") {
            steps {
                echo 'Building application...'
            }
        }

        stage("test") {
            steps {
                echo 'Running tests...'
            }
        }

        stage("SonarQube Analysis") {
            steps {
                withSonarQubeEnv('Sonar') { // Utilise le nom configuré
                    sh 'mvn clean package sonar:sonar'
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
                      odcInstallation: 'DP-Check'
                  
                  dependencyCheckPublisher pattern: 'dependency-check-report.html'
              }
        }  

        stage("deploy") {
            steps {
                echo 'Deploying application...'
            }
        }
    }
}
