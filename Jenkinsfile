node {

    stage("Git Clone"){

        git credentialsId: 'GIT_CREDENTIALS', url: 'https://github.com/mahson1/demo.git', branch: 'main'
    }
    stage('Compile stage') {
                bat "mvn -B -DskipTests clean package" 
        
    }

    stage('testing stage') {
                bat "mvn test"
        
    }

}
 
