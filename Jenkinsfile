pipeline {
    environment { 
        registry = "sbhalsing0/nodeapp" 
        registryCredential = 'Dockerhub' 
        dockerImage = ''
    }
    agent {
       label "docker"
    }
    stages {
        stage("checkout code") {
            steps {
               echo "Running in docker"
	           git branch: 'main',
		           credentialsId: 'Github_Sanket',
                   url: 'https://github.com/Sbhalsing0/jenkins-terraform.git'
            }
        }
        stage("build and test the project") {
            stages {
               stage("build") {
                   steps {
		      sh "pwd"
                   }
               }
               stage("test") {
                  steps { 
                      script { 
                         sh "ls"
                        }
                    }  
               }
            }
        }
    }
}
