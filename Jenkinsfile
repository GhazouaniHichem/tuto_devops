def gv
pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages{
        stage("Init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("Build JAR"){
            steps{
                script {
                    gv.buildJAR()
                }
            }
        }
        stage("Build Image"){
            steps{
                script {
                    gv.buildImage()
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