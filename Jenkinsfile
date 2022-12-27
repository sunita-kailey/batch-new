pipeline{
  agent any
  stages {
    stage('Build Application') {
      steps  {
        bat  'mvn clean install'
       }
      }
      stage('Test') {
        steps {
          echo 'test Aplication...'
          bat 'mvn test'
         }
        }
        
      stage('deploy CloudHub') {
              environment {
           ANYPOINT_CREDENTIALS = credentials('anypoint.creds')
         }
          steps {
            echo 'Deploying only because of code commit....'
            echo "deploying to ${params.env} environment "
            echo "worker is ${params.workerType}"
            bat 'mvn package deploy -DmuleDeploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -Denvironment=Sandbox -Dworkertype=Micro -Dworkers=1 -Dregion=us-west-2'
          }
        }
     }
   }      
           