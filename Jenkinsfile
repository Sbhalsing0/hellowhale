pipeline {
    agent any
    environment {
        AWS_ACCOUNT_ID=”746149138047”
        AWS_DEFAULT_REGION=”us-east-1”
        IMAGE_REPO_NAME=”crde-grafana”
        IMAGE_TAG=”4.0”
        REPOSITORY_URI = “${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}”
    }
   
    stages {
        
        //  stage('Logging into AWS ECR') {
        //     steps {
        //         script {
        //         sh "aws ecr get-login-password --region ${AWS_DEFAULT_REGION} | docker login --username AWS --password-stdin ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com"
        //         }
                 
        //     }
        // }
        
        // stage('Cloning Git') {
        //     steps {
        //         checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', url: 'https://github.com/sd031/aws_codebuild_codedeploy_nodeJs_demo.git']]])     
        //     }
        // }
  
    // Building Docker images
    stage('Building image') {
      steps{
        script {
        // docker.withRegistry("$", "ecr:us-east-1:credential-id") {
        // docker.image("your-image-name").push()
        docker.withRegistry('$REPOSITORY_URI', 'ecr:${AWS_DEFAULT_REGION}:aws_auth') {
        docker.image("${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}:${IMAGE_TAG}").pull()
            }
            }
        }
      }
    }
   
    // Uploading Docker images into AWS ECR
    stage('Pushing to ECR') {
     steps{  
         script {
                // sh "docker tag ${IMAGE_REPO_NAME}:${IMAGE_TAG} ${REPOSITORY_URI}:$IMAGE_TAG"
                // sh "docker push ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}:${IMAGE_TAG}"
                echo "Done"
         }
        }
      }
    }
}
