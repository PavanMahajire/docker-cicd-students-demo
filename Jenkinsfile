pipeline {
    agent any
    tools {
      maven 'maven3'
          }
    stages {
        stage('gitcheckout') {
            steps {
                echo 'git checkout'
            }
        }
        stage('mavenbuild') {
            steps {
                echo 'buoding artifacts'
                sh "mvn clean package"
            }
        }
        stage('dockerbuild') {
            steps {
                echo 'building image'
                sh 'docker build . -t pavanmahajire/image1:${BUILD_NUMBER}'
            }                     
        }
        stage('dockerpush') {
            steps {
                echo 'upload image'
                withCredentials([string(credentialsId: 'dockerpass', variable: 'dockerpass')]) {
                sh 'docker login -u pavanmahajire -p ${dockerpass}'
                sh 'docker push pavanmahajire/image1:${BUILD_NUMBER}'
                }
               
            }                     
        }
    }
}
