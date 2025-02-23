pipeline{
    agent any
    tools{
        maven "maven"
    }
    stages {
        stage("check out the repo"){
            steps{
                git branch: "ansible-sonar", url: "https://github.com/chumaedeogu/sample-web-application.git"
            }
            stage("manven package"){
            steps{
                bat 'mvn clean package'
            }
        }
    }
}