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
    stage('sonarQube Analysis'){
            steps{
                script{
                    
                
                    withSonarQubeEnv('sonar-scanner') {
                      bat '''
                       
                         %SCANNER_HOME%\\bin\\sonar-scanner -Dsonar.projectName=petclinic -Dsonar.projectKey=petclinic -Dsonar.java.binaries="C:\\Program Files\\Java\\
                        jdk-21\\bin\\java"
                            
                          '''  
                    }
            }
                
}
}


    