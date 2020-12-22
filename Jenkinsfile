pipeline{
    agent : any
    stages {
        stage ('compile'){
            steps{
                echo "Hello World"
            }
        }
    }
    
    }
    post: {
        always {
            sh 'echo build completed'
        }
        changed {
            sh 'echo build changed'
        }
    }
}