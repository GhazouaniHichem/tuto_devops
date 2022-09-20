pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages{
        stage("Build JAR"){
            steps{
                echo "========Building the application========"
                sh 'mvn package'
            }
        }
        stage("Build Image"){
            steps{
                echo "========Building the docker image========"
                withCredentials([usernamePassword(credentialsId: 'docker-hu-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                    sh 'docker build -t ghazouanihm/demo-app:jma-2.0 .'
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push ghazouanihm/demo-app:jma-2.0'
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "========Deploying the application========"
                
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