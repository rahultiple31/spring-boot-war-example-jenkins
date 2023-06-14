pipeline{
    agent any
    tools {
        maven 'MAVEN'
    }
    environment{
        PATH = "/usr/bin/mvn:$PATH"
    }
    stages{
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
                deploy adapters: [tomcat9(credentialsId: 'tomcatserverdetailes', path: '', url: 'http://192.168.50.20:8080')], contextPath: '/app', war: '**/*.war'
            }
        }
    }
    post{
        always{
            echo "========== always ========="
        }
        success{
            echo "========== pipeline executed successfully ========="
        }
        failure{
            echo "========== pipeline execution failed ========="
        }
    }
}
