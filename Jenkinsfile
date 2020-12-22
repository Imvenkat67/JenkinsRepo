pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
        upstream(upstreamProjects: 'proj1', threshold: hudson.model.Result.SUCCESS)
    }
    stages {
        stage('compile'){
            steps{
                echo "Hello World"
                exit 1
            }
        }
        stage('Test'){
            steps{
                echo "Test"
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
        fixed{
             sh 'echo wohha build is not triggerred'
        }
        failure{
             sh 'echo failed for a reason'
        }
        success{
            sh 'echo Project success'
        }
    }
}