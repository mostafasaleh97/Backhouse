pipeline {
    agent { label 'jenkins-slave' }

     
    stages {
        stage('build') {
            steps {
                script {
                     withCredentials([usernamePassword(credentialsId: 'mostafa', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                           sh """
                                docker login -u $USERNAME -p $PASSWORD
                                docker build -t mostafa001/firstbuild:${BUILD_NUMBER} .
                                docker push mostafa001/firstbuild:${BUILD_NUMBER}
                                echo ${BUILD_NUMBER} > ../bakehouse-build-number.txt
                           """
                }
            }
            }
        }
        stage('deploy') {
            steps {
                echo "deploy"
            }
        }
    }
}
