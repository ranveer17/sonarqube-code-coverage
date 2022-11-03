pipeline {
    agent any

    stages {
        stage('Clone sources') {
            steps {
                git branch: 'bad-code', url: 'https://github.com/ranveer17/sonarqube-code-coverage.git'
            }
        }

        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "./gradlew sonarqube"
                }
            }
        }
        stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
    }
}
