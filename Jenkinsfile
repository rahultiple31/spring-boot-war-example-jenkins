pipeline {
    agent any
     tools {
        maven 'MAVEN'
        }
    stages {
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("Deploy on Test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat-1', path: '', url: 'http://192.168.43.186:8080/')], contextPath: '/app', war: '**/*.war'
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
            emailext body: 'test...!!!!!!!!!!', subject: 'pipeline faield', to: 'rahultiple1@gmail.con'
        }
    }
}
