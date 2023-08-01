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
credentialsId: 'Nexus-User', 
groupId: 'com.web', 
nexusUrl: '3.93.10.183:8081/', 
nexusVersion: 'nexus3', 
protocol: 'http', 
repository: 'Java-Webapp1/', 
version: '4.0.0'
            }
        }
        stage('deploy to Tomcat Server'){
            steps{
                sshagent(['ubuntu']) {
                    sh """
                    scp -o StrictHostKeyChecking=no target/testPipeline.war ubuntu@34.238.50.219:/opt/tomcat/webapps/
                    ssh -o StrictHostKeyChecking=no ubuntu@34.238.50.219 stoptomcat
                    ssh -o StrictHostKeyChecking=no  ubuntu@34.238.50.219 startomcat
                    """
                }
            }
        }
    }
}