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

        stage("deploy"){
            steps{
                 sh '''
                 sudo chmod +x /var/lib/jenkins/workspace/Project-1/target/hello-world-0.0.1-SNAPSHOT.war
                 sudo java -jar /var/lib/jenkins/workspace/Project-1/target/hello-world-0.0.1-SNAPSHOT.war
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
