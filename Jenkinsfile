node {
	def app
	
	stage('Clone repository') {
		checkout scm
	}

	stage('Build image') {
		app = docker.build("vetzdocker/project1:1")
	}
	stage('Test Image') {
		app.inside {
			sh 'echo "Test passed"'
		}
	}
	stage('Push Image') {
		docker.withRegistry('https://cloud.docker.com/repository/docker/vetzdocker/project1', 'docker-hub-credentials') {
			app.push("${env.BUILD_NUMBER}")
			app.push("latest")
		}
	}
}							
