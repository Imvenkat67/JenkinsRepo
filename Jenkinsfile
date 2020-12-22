pipeline {
    agent any
    triggers {
        upstream(upstreamProjects:{'proj1'})
    }
    stages {
        stage('compile'){
            steps{
                echo "Hello World"
            }
        }
    }
      
    post {
        always {
            sh 'echo build completed'
        }
        changed {
            sh 'echo build changed'
        }
    }
}