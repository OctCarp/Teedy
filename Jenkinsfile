pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                sh 'mvn clean install -B --no-transfer-progress'
            }
        }
        stage('Doc'){
            steps {
                junit '**/target/surefire-reports/TEST-*.xml'
            }
        }
        stage('pmd') {
            steps {
                sh 'mvn pmd:pmd'
            }
        }
        stage('Test Report') {
            steps {
                sh 'mvn javadoc:jar'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/target/site/**', fingerprint: true
            archiveArtifacts artifacts: '**/target/**/*.jar', fingerprint: true
            archiveArtifacts artifacts: '**/target/**/*.war', fingerprint: true
        }
    }
}