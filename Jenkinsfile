pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('Checkout'){
            steps{
                git credentialsId: 'Jenkins', url: 'git@github.com:devopsmoon/Java-App-1.git'
            }
        }
    }
}