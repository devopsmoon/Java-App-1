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
        stage('build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Sonarqube Analysis'){
            steps{
                withSonarQubeEnv(installationName: 'sonar', credentialsId: 'sonar'){
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Nexus Pull'){
            steps{
                nexusArtifactUploader artifacts: [
[
artifactId: 'testPipeline', 
classifier: '', 
file: 'target/testPipeline.war', 
type: 'war'
]
], 
credentialsId: 'nexus_user', 
groupId: 'com.web', 
nexusUrl: '54.227.246.158:8081', 
nexusVersion: 'nexus3', 
protocol: 'http', 
repository: 'Java-App/', 
version: '4.0.0'
            }
        }
    }
}