node {

    environment { 
        registry = "mahson87/demo-0.0.2-snapshot" 
        registryCredential = 'dockerhub_id' 
        dockerImage = '' 
    }
  stage ('Build') {
    git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/mahson1/springboot-kube-example.git', branch: 'main'
    def mvn_version = 'Maven'
    withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
     sh "mvn clean package"
    }// withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
  }
  
  stage("Docker build"){
        sh """
          /usr/local/bin/docker version
          """
        sh """
        /usr/local/bin/docker build -t demo-0.0.2-snapshot.jar .
        """
        sh """
        /usr/local/bin/docker image list
        """
        sh """
        /usr/local/bin/docker tag demo-0.0.2-snapshot.jar mahson87/demo-0.0.2-snapshot:demo-0.0.2-snapshot
        """
    }
  
  stage("Docker Login"){
        withCredentials([string(credentialsId: 'DOCKER_HUB_PASSWORD', variable: 'PASSWORD')]) {
            sh '/usr/local/bin/docker login -u mahson87 -p Shop3r$44'
        }
    } 
  stage("Push Image to Docker Hub"){
        sh '/usr/local/bin/docker push  mahson87/demo-0.0.2-snapshot:demo-0.0.2-snapshot'
    }
}
