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
                sh 'docker built . -t pavanmahajire/image1:${BUILD_NUMBER}'
            }
                               
        }
    }
}
