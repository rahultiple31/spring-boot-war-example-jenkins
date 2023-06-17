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
                sshagent(['deploy_user']) {
                    deploy adapters: [tomcat9(credentialsId: 'tomcatserver', path: '', url: 'http://192.168.50.20:8080')], contextPath: '/app', war: '**/*.war'
                }
            }  
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
             slackSend channel: 'youtubejenkins', message: 'Success'
        }
        failure{
            echo "========pipeline execution failed========"
             slackSend channel: 'youtubejenkins', message: 'Job Failed'
        }
    }
}
