pipeline {
    environment { 
        registry = "sbhalsing0/nodeapp" 
        registryCredential = 'Dockerhub' 
        dockerImage = ''
    }
    agent {
       label "docker_slave_mvn"
    }
    stages {
        stage("checkout code") {
            steps {
               echo "Running in docker"
	           git branch: 'main',
		           credentialsId: 'Github_Sanket',
                   url: 'https://github.com/Sbhalsing0/jenkins-terraform.git'
               sh "ls -lat"
            }
        }
        stage('Building our image') {
            steps {
                script {
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
        stage('Building our image') {
            steps { 
                script { 
                    docker.withRegistry( '', registryCredential ) { 
                        dockerImage.push()
                    }
                } 
            }
        }
        stage('Deploy Docker Image') {
            steps {
                sh "docker --version"
            }
        }
    }
}
