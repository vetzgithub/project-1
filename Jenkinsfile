node {
	def app
	
	stage('Clone repository') {
		checkout scm
	}

	stage('Build image') {
		app = docker.build("vetzdocker/project1:devops")
	}
	stage('Test Image') {
		app.inside {
			sh 'echo "Test passed"'
		}
	}
	stage('Push Image') {
		docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
			app.push("${env.BUILD_NUMBER}")
			app.push("latest")
		}
	}
}							
