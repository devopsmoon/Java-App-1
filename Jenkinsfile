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
        stage('Nexus Push'){
            steps{
                nexusArtifactUploader artifacts: [
[
artifactId: 'testPipeline', 
classifier: '', 
file: 'target/testPipeline.war', 
type: 'war'
]
],
credentialsId: 'nexus', 
groupId: 'com.web', 
nexusUrl: '54.227.227.198:8081', 
nexusVersion: 'nexus3', 
protocol: 'http', 
repository: 'Java-App-Repo/', 
version: '1.0.1'
            }
        }
    }
}