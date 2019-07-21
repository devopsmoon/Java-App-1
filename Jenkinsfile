node {
	stage('SCM checkout'){
		git 'https://github.com/RAJKRANJ/jenkinfileTest.git'
	}
	stage('compile-package'){
		def mvnHome = tool name: 'M3', type: 'maven'
		sh "${mvnHome}/C:\Users\RajeshRanjan\Desktop\Dev_ops software\apache-maven-3.6.1-bin\apache-maven-3.6.1\bin"
	}
	
}
