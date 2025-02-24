pipeline {
    agent any
    tools {
        maven 'maven'  // Ensure "maven" is installed in Jenkins tools
     
    }
      environment {
        SCANNER_HOME = tool 'sonar-scanner'
    }
    
    stages {
        
        stage('Unit Testing') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    withSonarQubeEnv('sonar-scanner') {  // Ensure SonarQube is configured in Jenkins
                        bat """
                            "%SCANNER_HOME%\\bin\\sonar-scanner" ^
                            -Dsonar.projectName=petclinic1 ^
                            -Dsonar.projectKey=petclinic1 ^
                            -Dsonar.java.binaries="C:\\Program Files\\Java\\jdk-21\\bin\\java"
                        """
                    }
                }
            }
        }
        stage("scan the fs"){
            steps{
                bat 'trivy fs --format table -o report.txt .'
            }
        }
        stage("build the docker image"){
            steps{
                script{
                withDockerRegistry(credentialsId: 'docker4') {
                 bat ''' 
                 docker build -t chumaedeogu/connect .
                 docker push chumaedeogu/connect
                 
                 '''
              }
            }
        }
    }

}
}