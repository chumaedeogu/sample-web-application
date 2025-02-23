pipeline{
    agent any
    tools{
        maven "maven"
    }
    stages{
        stage("unit testing"){
            steps{
                bat 'mvn clean build'
            }
        }
    }
}

    