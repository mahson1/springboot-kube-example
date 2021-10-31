node {

    stage("Git Clone"){

        git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/mahson1/springboot-kube-example.git', branch: 'main'
    }
    stage('Compile stage') {
                sh "mvn -B -DskipTests clean package" 
        
    }

    stage('testing stage') {
                sh "mvn test"
        
    }

}
 
