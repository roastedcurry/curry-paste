node('master') {
    echo 'checking out scm...'
    checkout scm
}

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'building...'
                sh 'printenv'
                sh 'python3 devops/testing/jenkins_master_test/main.py'
            }
        }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
            steps {
                echo 'deploying...'
            }
        }
    }
}