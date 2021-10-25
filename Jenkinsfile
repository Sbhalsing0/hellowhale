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
               sh "ls -la"
            }
        }
        stage("build and test the project") {
            stages {
               stage("build") {
                   steps {
                      script {
                          dockerImage = docker.build registry + ":$BUILD_NUMBER"
                        }
                   }
               }
               stage("test") {
                  steps { 
                      script { 
                          docker.withRegistry( '', registryCredential ) { 
                               dockerImage.push()
                            }
                        }
                    }  
               }
            }
        }
    }
}
