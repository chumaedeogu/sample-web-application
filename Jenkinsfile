pipeline{
    agent any
    tools{
        maven "maven"
          }
    stages{
        stage("git checkout"){
            steps{
                git branch: "ansible-sonar", url: "https://github.com/chumaedeogu/sample-web-application.git"
            }
                          } 
         stage("unit test")
            {
            steps{
                bat 'mvn clean build'
                 }
            )
            
    }
}
