pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage("Build & Analyse avec SonarQube") {
            steps {
                sh 'mvn -v'
            }
        }
    }
}
