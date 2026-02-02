pipeline{
  agent any
  stages{
    stage('clone'){
      steps{
        git 'https://github.com/Gowri0126/javaapp.git'
      }
    }
    stage('Build'){
      sh 'mvn clean package'
    }
  }
   stage('Docker build'){
     sh 'docker build -t javaapp:1.0 .'
   }
}
  stage('Deploy'){
    sh 'docker service create --name javaapp_service/javaapp:1.0'
  }
}
}}
