pipeline {
  agent any
  stages {
    stage ('test') {
      steps {
        echo "Hello, World"
      }
    }
    stage ('Build  Docker image') {
      steps {
        sh '''
            docker build --rm -t andriihackaton .
        '''
      }
    }
    stage ('Login to ECR') {
      steps {
        sh '''
            $(aws ecr get-login --no-include-email --region us-east-2)
        '''
      }
    }
    stage ('Tag and push docker image') {
      steps {
        sh '''
           docker tag andriihackaton:latest 881926258290.dkr.ecr.us-east-2.amazonaws.com/andriihackaton:latest;
           docker push 881926258290.dkr.ecr.us-east-2.amazonaws.com/andriihackaton:latest           
        '''
      }
    }
  }
}
