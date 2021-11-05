pipeline { 
    environment {
        registry = "mahson87/demo-0.0.2-snapshot"
        registryCredential = 'dockerhub_id'
        dockerImage = '' 
    }
    agent any 
    stages { 
        stage('Cloning our Git') { 
            steps { 
                git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/mahson1/springboot-kube-example.git', branch: 'main'
            }
        }
        stage('Building our image') {
            steps {
                script {
                    dockerImage = /usr/local/bin/docker.build registry + ":$BUILD_NUMBER"
                }
            }
        }
        stage('Deploy our image') { 
            steps {
                script {
                    /usr/local/bin/docker.withRegistry( '', registryCredential ) { 
                        dockerImage.push()
                    }
                } 
            }
        }
        stage('Cleaning up') {
            steps {
                sh "/usr/local/bin/docker rmi $registry:$BUILD_NUMBER" 
            }
        }
    }
}
