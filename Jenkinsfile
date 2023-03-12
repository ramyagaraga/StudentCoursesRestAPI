pipeline {
    agent { label 'docker' }
    triggers { 
        pollSCM('* * * * *')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/ramyagaraga/StudentCoursesRestAPI',
                    branch: 'develop'
            }
        }
        stage('build') {
            steps {
                sh 'docker image build -t ramyagaraga/src:latest .'
            }
        }
        stage('scan and push') {
            steps {
                sh 'echo docker scan ramyagaraga/src:latest'
                sh 'docker image push ramyagaraga/src:latest'
            }
        }
    }

}