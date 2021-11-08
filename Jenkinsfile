@Library('service_workflow_library@master') _

pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: jnlp
            image: jenkins/inbound-agent:4.7-1
            command:
            - cat
            tty: true
        '''
    }
  }
  stages {
    stage('build over jnlp agent') {
      steps {
        container('jnlp') {
          sh 'mvn -version'
      }
    }
      steps {
        container('jnlp') {
    		git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/mahson1/springboot-kube-example.git', branch: 'main'
   	 	    def mvn_version = 'Maven'
    		withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
     			sh "mvn clean package"
    		}// withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
      }
    }
  }


}
