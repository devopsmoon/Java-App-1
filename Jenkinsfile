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
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Sonarqube Analysis'){
            steps{
                withSonarQubeEnv(installationName:'sonar',credentialsId: 'sonar'){
                 sh 'mvn sonar:sonar'
                }
                
            }
        }
    }
}