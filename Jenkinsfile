pipeline{
   agent any
  tools{
    maven 'maven'
  }
  stages{
    stage ('Initialize'){
    steps{
      sh '''
      echo "PATH = {$PATH}"
      echo "M2_HOME = {M2_HOME}"
      '''
    }
    }
    stage ('build'){  
      steps{
      sh ' mvn clean package'
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
