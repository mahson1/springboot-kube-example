pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: jnlp
            image: mahson87/jenkins-agent:1.0
            command:
            - cat
            tty: true
        '''
    }
  }
  stages {
	  
	  
    stage('Run maven') {
      steps {
        container('maven') {
	sh "mvn clean package"
        }
      }
    }

   stage('BUILD DOCKER IMANGE AND PUSH') {
      steps {
        container('jnlp') {
	 sh """
          docker version
          """
        sh """
        docker build -t demo-0.0.2-snapshot.jar .
        """
        sh """
        docker image list
        """
        sh """
        docker tag demo-0.0.2-snapshot.jar mahson87/demo-0.0.2-snapshot:demo-0.0.2-snapshot
        """
        }
      }
    }


  }
}
