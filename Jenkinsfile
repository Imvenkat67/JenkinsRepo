pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
        upstream(upstreamProjects: 'proj1', threshold: hudson.model.Result.SUCCESS)
    }
    options { 
        buildDiscarder(logRotator(numToKeepStr: '2')) 
        disableConcurrentBuilds()
        retry(2)
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
                exit 1
                
            }
        }
        stage('Test'){
          environment {
           JAVA_VERSION ='1.7'
           GITHUB_CREDS= credentials('github');
    }
            steps{
                echo "Test"
                sh 'echo $JAVA_VERSION'
                sh 'echo $GITHUB_CREDS'
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