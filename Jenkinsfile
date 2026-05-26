pipeline{
    agent any
    stages{
         stage("GitHub checkout") {
            steps {
                script {
 
                    git branch: 'main', url: 'https://github.com/oyebodeabi-a11y/Terraform_AWS_Assignment-2' 
                }
            }
        }
        stage("Build docker on going"){
            steps{
                sh 'printenv'
                sh 'git version'
                sh 'docker build . -t bims15/imag5.0'
            }
        }
         stage("push image to DockerHub"){
            steps{

               script {
                  
                 withCredentials([string(credentialsId: 'dockerID', variable: 'dockerID')]) {
                    sh 'docker login -u bims15 -p ${dockerID}'
            }
              sh 'docker push bims15/imag5.0:latest'
            }
        }
    }
    }
}