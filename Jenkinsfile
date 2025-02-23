pipeline{
    agent any
    tools{
        maven "maven"
        sonarScanner 'sonar-scanner'
    }
    environment{
        sonar = tool{
            'sonar-scanner'
        }
    }
    stages{
        stage("unit testing"){
            steps{
                bat 'mvn clean package'
            }
        }
        stage("static analysis with sonarqube"){
            steps{
              withSonarQubeEnv() {
           bat "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=test"
             }
            }
        }
    }
}

    