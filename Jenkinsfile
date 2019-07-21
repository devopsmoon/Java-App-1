jsp {
	stage('SCM checkout'){
		git 'https://github.com/RAJKRANJ/jenkinfileTest.git'
	}
	stage('compile-package'){
		def mvnHome = tool name: 'M3', type: 'maven'
		sh 'mvn test'
	}
	
}
