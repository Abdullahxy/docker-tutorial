pipeline {
  
  agent any
  
  options {
   
    buildDiscarder(logRotator(numToKeepStr:'5'))
    
  }
  
  environment {
    
   DOCKERHUB_CREDENTIALS = credentials('Abdullahxy-dockerhub')
    
  }
  
  stages {
    
    stage('initialize') {
      
      steps {
        
        script{
          def dockerHome = tool 'docker'
          env.PATH = "${dockerHome}/bin:${env.PATH}"
        }
      }
        
    }
    
    stage("build") {
      
      steps {
        
        echo 'building the Image from Dockerfile...'
        sh 'docker build -t Abdullahxy/twn-demo-app:latest .'
        
      }
      
    }
    
    stage("login") {
      
      steps {
        
        echo 'logging into DockerHub...'
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        
      }
    }
    
    stage("push") {
      
      steps {
        
        echo 'deploying the application...'
        sh 'docker push Abdullahxy/twn-demo-app:latest'
        
      }
    }
  }
  
  post {
   
    always {
     
      sh 'docker logout'
      
    }
    
  }
  
}
