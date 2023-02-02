pipeline {
    agent { label 'jenkins-slave' }

    } 
    stages {
        stage('build') {
            steps {
                script {
                   if (params.ENV == "release") {
                       withCredentials([usernamePassword(credentialsId: 'mostafa', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                           sh """
                                docker login -u $USERNAME -p $PASSWORD
                                docker build -t mostafasaleh97/firstbuild:${BUILD_NUMBER} .
                                docker push mostafasaleh97/firstbuild:${BUILD_NUMBER}
                                echo ${BUILD_NUMBER} > ../bakehouse-build-number.txt
                           """
                       }
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
