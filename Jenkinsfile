pipeline {
  agent {
    kubernetes {
      yaml '''
    apiVersion: v1
    kind: Pod
    metadata:
      name: sprintboot-test-jnlp
    spec:
      containers:
      - name: jnlp
        image: jenkins/inbound-agent:4.3-4-jdk11
        command: ["sleep", "10000"]
    '''
    }
  }
  stages {
    stage('Run maven') {
      steps {
        container('maven') {
		    //git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/mahson1/springboot-kube-example.git', branch: 'main'
    		   //def mvn_version = 'Maven'
 		   //withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
	sh "mvn clean package"
		    //}// withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
        }
      }
    }
  }

}
