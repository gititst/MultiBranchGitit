pipeline {
    agent any

    stages {
        stage('Copy Test Results'){
            steps {
                bat 'cd'
                //bat 'mkdir reports'
                bat 'xcopy /S ..\\..\\hpdevops-discovery-demoapp-master\\reports\\* reports'
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
