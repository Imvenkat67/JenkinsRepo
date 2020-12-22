pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
        upstream(upstreamProjects: 'proj1', threshold: hudson.model.Result.SUCCESS)
    }
    environment {
        JAVA_VERSION ='1.8'
        GITHUB_CREDS= credentials('github');
    }
    stages {
        stage('compile'){
            steps{
                sh 'echo Hello World'
                sh 'echo $JAVA_VERSION'
                sh 'echo GITHUB_USER : $GITHUB_CREDS'
                
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