pipeline {
    agent { label 'node1' }
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
        stage('deploy to st') {
            steps {
                sh 'kubectl apply -f ./K8s/mysql.yml'
                sh 'kubectl apply -f ./K8s/flask.yml'
                sh 'sleep 10s'
                sh 'kubectl get svc'
            }
        }    
    }

}