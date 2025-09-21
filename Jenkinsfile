
pipeline{
    agent {label 'linux'}
    parameters {
      choice(name:"environment",choices:['DEV','UAT'],description:"ENVIRONMENT TO DEPLOY")
    }
    options { 
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    stages{
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }
    post{
        always{
            echo "Pipeline ran in ${params.environment}"
        }
        success{
            echo "built and tested"
        }
        failure{
            echo "pipeline failed"
        }
    }

}
        
        
            
                       
    
