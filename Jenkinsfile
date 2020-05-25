@Library('jenkins-pipeline-shared-libraries')_

pipeline {
    agent {
        label 'kie-rhel7 && !master'
    }
    options {
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '', numToKeepStr: '10')
        timeout(time: 5, unit: 'MINUTES')
    }
    stages {
        stage('Initialize') {
            steps {
                sh 'printenv'

            }
        }
        stage('Build rhba') {
            build job: 'simple-jenkins-project/master', propagate: false, wait: false
        }
    }
    post {
        cleanup {
            cleanWs()
        }
    }
}