pipeline {
	agent any
	
	stages{
		stage('Code'){
			steps{
				git url: 'https://github.com/mcollins1010/node-todo-cicdupdate.git', branch: 'master'
			}
		}
		stage('Build'){
			steps{
				sh 'docker build -t collinzo1010/nodeto:latest .'
			}
		}
		stage('Push'){
			steps{
				withCredentials([usernamepassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]){
				sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
				sh 'docker push collinzo1010/nodeto:latest'
				}
			}
		}
			
	}

}
