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
                echo "$BUILD_ID"
                '''
            }
        }

        stage("test"){
            steps{
                 sh 'mvn test'
            }
        }

        stage("build docket images"){
            steps{
                 sh '''
                 docker build -t app .
                 '''
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
