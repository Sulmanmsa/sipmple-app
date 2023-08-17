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
                deploy adapters: [tomcat9(credentialsId: '2c1d507b-4b59-47d9-a7b3-3c204d4b1cf8', path: '', url: 'http://localhost:9494/')], contextPath: 'simple-app', war: '**/*.war'
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
