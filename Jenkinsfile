node {

    stage("Git Clone"){

        git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/mahson1/springboot-kube-example.git', branch: 'main'
    }
    stage('Compile stage') {
               sh "mvn clean verify"
        
    }

    stage('testing stage') {
              sh "mvn test"
        
    }

}

node {
  stage ('Build') {
    git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/mahson1/springboot-kube-example.git', branch: 'main'
    withMaven {
      sh "mvn clean verify"
    } // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
  }
}
 
