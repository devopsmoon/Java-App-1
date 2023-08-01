pipeline{
    agent any
    tools{
        maven 'maven'
    }
    options{
       buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '5')) 
    }
    stages{
        stage('Checkout'){
            steps{
                git credentialsId: 'Jenkins-user', url: 'git@github.com:devopsmoon/Java-App-1.git'
            }
        }
        stage('Test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Sonar Analysis'){
            steps{
            withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'Sonar-Token'){
                sh 'mvn sonar:sonar'
            }
            }
            
        }
    }
}