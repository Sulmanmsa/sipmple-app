pipeline{
    agent any
    tools{
        maven 'Maven'
    }
    stages{
        stage("Test"){
            steps{
                bat 'mvn test'
            }
            
        }
        stage("build"){
            steps{
                bat 'mvn clean package'
            }
            
        }
         stage("deploy"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'deployTest', path: '', url: 'http://localhost:9494/')], contextPath: 'sipmple-app', war: '**/*.war'
            }
            
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
