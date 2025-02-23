pipeline {
    agent any
    tools {
        maven 'maven'  // Ensure "maven" is installed in Jenkins tools
        sonar 'Sonar-Scanner'  // Use correct SonarQube tool name
    }
    stages {
        stage('Setup Environment') {
            steps {
                script {
                    env.SCANNER_HOME = tool 'SonarQube Scanner'  // Get scanner path
                }
            }
        }
        stage('Unit Testing') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    withSonarQubeEnv('SonarQube') {  // Ensure SonarQube is configured in Jenkins
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
    }
}
