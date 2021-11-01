node {
  stage ('Build') {
    git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/mahson1/springboot-kube-example.git', branch: 'main'
    def mvn_version = 'Maven'
    withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
     sh "mvn clean package"
    }// withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
  }
  
  stage("Docker build"){
        sh 'docker version'
        sh 'docker build -t demo-0.0.1-SNAPSHOT.jar .'
        sh 'docker image list'
        sh 'docker tag jhooq-docker-demo mahson87/demo-0.0.1-SNAPSHOT.jar:demo-0.0.1-SNAPSHOT.jar'
    } 
}

