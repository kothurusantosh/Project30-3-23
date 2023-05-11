
node {
	def application = "tomcatimage"
	def dockerhubaccountid = "neelimadevi909"
	stage('Clone repository') {
		checkout scm
	}

	stage('Build image') {
		app = docker.build("${dockerhubaccountid}/${application}:${BUILD_NUMBER}")
	}

	stage('Push image') {
		withDockerRegistry([ credentialsId: "DockerHub_cred", url: "" ]) {
		app.push()
		
	}
	}

	stage('Deploy') {
		sh ("docker run -d -p 81:8080 ${dockerhubaccountid}/${application}:${BUILD_NUMBER}")
	}
	
	
}
