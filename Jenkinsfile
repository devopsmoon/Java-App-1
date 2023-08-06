pipeline{
    agent any
    tools {
        maven 'maven'
    }
    options{
    buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '5'))
    }
    
    stages{
        stage('Checkout'){
            steps{
                git branch: 'master', credentialsId: 'jenkins', url: 'git@github.com:devopsmoon/Java-App-1.git'
                echo "welcome to devops world"
            }
        }
    }
}