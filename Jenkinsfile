pipeline {
  agent any
  tools {
    // a bit ugly because there is no `@Symbol` annotation for the DockerTool
    // see the discussion about this in PR 77 and PR 52: 
    // https://github.com/jenkinsci/docker-commons-plugin/pull/77#discussion_r280910822
    // https://github.com/jenkinsci/docker-commons-plugin/pull/52
    'org.jenkinsci.plugins.docker.commons.tools.DockerTool' '18.09'
  }
  environment {
    DOCKER_CERT_PATH = credentials('id-for-a-docker-cred')
  }
  stages {
    stage('foo') {
      steps {
        sh "docker version" // DOCKER_CERT_PATH is automatically picked up by the Docker client
      }
    }
  }
}






// pipeline {
  
//   agent any
  
//   options {
   
//     buildDiscarder(logRotator(numToKeepStr:'5'))
    
//   }
  
//   environment {
    
//    DOCKERHUB_CREDENTIALS = credentials('Abdullahxy-dockerhub')
    
//   }
  
//   stages {
    
//     stage('initialize') {
      
//       steps {
        
//         script{
//           def dockerHome = tool 'docker'
//           env.PATH = "${dockerHome}/bin:${env.PATH}"
//         }
//       }
        
//     }
    
//     stage("start") {
      
//       steps {
        
//         echo 'Starting docker daemon..'
//         sh 'dockerd'
        
//       }
      
//     }
    
//     stage("build") {
      
//       steps {
        
//         echo 'building the Image from Dockerfile...'
//         sh 'docker build -t abdullahxy/twn-demo-app:latest .'
        
//       }
      
//     }
    
//     stage("login") {
      
//       steps {
        
//         echo 'logging into DockerHub...'
//         sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        
//       }
//     }
    
//     stage("push") {
      
//       steps {
        
//         echo 'deploying the application...'
//         sh 'docker push abdullahxy/twn-demo-app:latest'
        
//       }
//     }
//   }
  
//   post {
   
//     always {
     
//       sh 'docker logout'
      
//     }
    
//   }
  
// }
