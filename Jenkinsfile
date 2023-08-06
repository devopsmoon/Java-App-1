pipeline{
    agent any
    tools {
        maven 'maven'
    }
    stages{
        stage('Checkout'){
            steps{
                git branch: 'main', credentialsId: 'jenkins', url: 'git@github.com:devopsmoon/Java-App-1.git'
            }
        }
    }
}