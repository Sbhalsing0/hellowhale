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
		   sh "docker --version"
		   sh "ls"
		   sh "chown jenkins:docker /var/run/docker.sock"
            }
        }
        stage("build and test the project") {
            stages {
               stage("build") {
                   steps {
		      sh "docker build -t demo ."
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
