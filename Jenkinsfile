pipeline{
    agent any

    stages{
        stage('Git checkout code') {
            steps {
                git 'https://github.com/rahultiple31/spring-boot-war-example-jenkins.git'
            }
        }


        stage("build code"){
            steps{
                sh '''
                mvn clean package
                '''
            }
        }



        stage("test"){
            steps{
                 sh 'mvn test'
            }
        }


    }
    post{
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
