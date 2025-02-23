pipeline{
    agent any
    stages{
        stage("check out")
        {
            steps{
                git branch: "ansible-sonar", url: "https://github.com/chumaedeogu/sample-web-application.git"
            }
        }
         stage("Unit test")
        {
            steps{
                bat 'mvn clean build'
            }
        }
    }
    }
}