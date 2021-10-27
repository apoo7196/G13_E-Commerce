pipeline {

  agent any
  environment {
    //adding a comment for the commit test
    DEPLOY_CREDS = credentials('deploy-anypoint-user')
    MULE_VERSION = '4.3.0'
    BG = "Apisero"
    WORKER = "Micro"
  }
  stages {
    stage('Build') {
      steps {
            bat 'mvn deploy -DmuleDeploy'
      }
    }

    stage('Test') {
      steps {
          bat "mvn test"
      }
    }

     stage('Deploy Development') {
      environment {
        ENVIRONMENT = 'Sandbox'
        APP_NAME = 'sandbox-g13ecommerce-AK'
      }
      steps {
            bat 'mvn deploy -DmuleDeploy -Dmule.version="4.3.0" -Danypoint.username="apoorva1234" -Danypoint.password="Apoorva@0701" -Dcloudhub.app="sandbox-g13ecommerce-AK" -Dcloudhub.environment="Sandbox" -Dcloudhub.bg="Apisero%" -Dcloudhub.worker="Micro"'
      }
    }
    
  }

  tools {
    maven 'MAVEN_HOME'
  }
}