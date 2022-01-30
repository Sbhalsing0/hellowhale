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
		      sh "ls"
		      sh "chmod a+x setup_env.sh"
		      sh "./setup_env.sh"
		      sh "cat .env"
                   }
               }
               stage("test") {
                  steps { 
                      script { 
			sshagent(['ginger-onprem']) {
    				sh 'echo "Adding new file" >> new.txt'
    				sh 'scp new.txt vasirm01@dev-ginger-504.np.st1.yellowpages.com:/home/vasirm01/.'
			      }
                        }
                    }  
               }
            }
        }
    }
}
