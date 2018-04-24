pipeline {
    agent any

    stages {
        stage('Copy Test Results'){
            steps {
                bat 'cd'
                bat 'mkdir -p $WORKSPACE/reports'
                bat 'cd ../.. ; cd; copy -R hpdevops-discovery-demoapp-master/reports/. $WORKSPACE/reports'
                bat 'sleep 2'
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
