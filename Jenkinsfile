pipeline {
    agent any
    tools {
        sonarQube 'Sonarqube-Scanner'
    }
    stages {
        stage('SonarQube Analysis') {
            steps {
                sh '''
                sonar-scanner \
                  -Dsonar.projectKey=MonProjet \
                  -Dsonar.sources=. \
                  -Dsonar.host.url=http://localhost:9000 \
                  -Dsonar.login=squ_16937dd9ef98cbe457a6505f433226d56812403f
                '''
            }
        }
    }
}

