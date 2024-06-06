pipeline{
   agent any
  tools{
    maven 'maven'
  }
  stages{
    stage ('Initialize'){
    steps{
     echo 'Initializing the build environment...'
       checkout scm
    }
    }
    stage ('build'){  
      steps{
      sh ' mvn clean install'
      }
    }
   stage ( 'Deploy to tomcat' ){
    steps{
    sshagent(['tomcat']){
    sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@54.158.204.54:/home/ubuntu/prod/apache-tomcat-10.1.24/webapps/webapp.war'
    }
    }
   }
  }
}
