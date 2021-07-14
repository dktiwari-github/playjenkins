pipeline {

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/dktiwari-github/playjenkins', branch:'test-deploy-stage'
      }
    }

    stage('Deploy App') {
      steps {
        script {
          kubernetesDeploy(configs: "nginx.yaml", kubeconfigId: "kubeConfig")
        }
          post {
              success{
                  emailext body: 'Deployment is successful', recipientProviders: [developers()], subject: 'playjenkins', to: 'dheeraj.tiwari@afourtech.com'
              }
          }
       }
    }
  }
}
