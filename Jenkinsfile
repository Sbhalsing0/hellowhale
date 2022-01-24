pipeline {
    environment { 
        AWS_ACCOUNT_ID=”746149138047”
        AWS_DEFAULT_REGION=”us-east-1”
        IMAGE_REPO_NAME=”crde-grafana”
        IMAGE_TAG=”4.0”
        REPOSITORY_URI = “${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}”
    }
    agent {
       label "docker"
    }
    stages {
        stage("Logging into AWS ECR") {
            steps {
            docker.withRegistry('$REPOSITORY_URI', 'ecr:${AWS_DEFAULT_REGION}:aws_auth') {
                docker.image("${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}:${IMAGE_TAG}").pull()
            }
		//    sh "aws ecr get-login-password — region ${AWS_DEFAULT_REGION} | docker login — username AWS — password-stdin ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com"
		//    sh "docker pull ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}:${IMAGE_TAG}"
            }
        }
    }
        stage("post") {
            stages {
               stage("post") {
                   steps {
		      echo "Successfully Image Pull"
                }
            }
        }
    }
}
