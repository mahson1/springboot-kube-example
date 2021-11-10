pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: maven
            image: jenkins/jnlp-agent-docker:latest
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




  }
}
