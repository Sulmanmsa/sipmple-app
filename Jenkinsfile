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
                deploy adapters: [tomcat9(credentialsId: '8e7fe36e-72a2-4c9e-bec7-c2b127bb9732', path: '', url: 'http://localhost:9494/')], contextPath: 'simple-app', war: '**/*.war'
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
