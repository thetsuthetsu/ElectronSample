pipeline {
    agent any
    stages {
        stage('PWD') {
            steps {
                sh 'pwd'
            }
        }
        stage('LS') {
            steps {
                sh 'ls -l'
            }
        }
        stage('DETECT') {
            steps {
                synopsys_detect detectProperties: '--blackduck.url=https://192.168.150.213 --blackduck.username=sysadmin --blackduck.password=blackduck --blackduck.trust.cert=true --detect.blackduck.signature.scanner.individual.file.matching=ALL --snippet-matching-all-source', downloadStrategyOverride: [$class: 'ScriptOrJarDownloadStrategy']
            }
        }
    }
    post {
        always {
            sendMail(currentBuild.currentResult)
        }
    }
}
