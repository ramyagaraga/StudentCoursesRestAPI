pipeline {
    agent { label 'docker' }
    triggers { 
        pollSCM('* 23 * * 1-5')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/ramyagaraga/StudentCoursesRestAPI',
                    branch: 'sprint_1_release'
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