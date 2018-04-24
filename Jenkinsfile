pipeline {
    agent any

    stages {
        stage('Copy Test Results'){
            steps {
                sh 'cd'
                sh 'mkdir -p $WORKSPACE/reports'
                sh 'cd ../.. ; cd; copy -a hpdevops-discovery-demoapp-master/reports/. $WORKSPACE/reports'
                sh 'sleep 2'
            }
        }
        stage('Say Hi'){
            steps {
                echo 'Hello World'
            }
        }
   }

    post {
        always {
            step([$class: 'XUnitBuilder',
                thresholds: [[$class: 'FailedThreshold', unstableThreshold: '1']],
                tools: [[$class: 'JUnitType', pattern: 'reports/resultsSet1/TEST*.xml']]])
        }
    }
}
