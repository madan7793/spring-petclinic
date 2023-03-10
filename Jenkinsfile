pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/madan7793/spring-petclinic.git']]])            

          }
        }
        
        stage ("terraform init") {
            steps {
                sh ('terraform init') 
            }
        }
        
        stage ("terraform  plan") {
            steps {
                sh ('terraform plan') 
            }
        }

        stage('Approval') {
            when {
                not {
                    equals expected: true, actual: params.autoApprove
                }
            }
        }

        stage ("terraform apply") {
            steps {
                sh ('terraform apply ')
            }
        }
                
    }
}
