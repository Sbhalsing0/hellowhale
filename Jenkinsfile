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
		echo "Sanket Pipeline"
	           git branch: 'main',
		           credentialsId: 'Github_Sanket',
                   url: 'https://github.com/Sbhalsing0/jenkins-terraform.git'
            }
        }
        stage("build and test the project") {
            stages {
               stage("build") {
                   steps {
		      sh "ls"
		      sh "chmod a+x setup_env.sh"
		      sh "./setup_env.sh"
		      sh "cat .env"
                   }
               }
               stage("test") {
                  steps { 
                      script { 
			sshagent(['local_ubuntu']) {
    				sh 'echo "Adding new file" >> new.txt'
    				//sh 'scp new.txt ubuntu@192.168.0.110:/home/ubuntu/.'
			      }
                        }
                    }  
               }
            }
        }
    }
}
