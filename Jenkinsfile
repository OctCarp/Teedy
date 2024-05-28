pipeline {
agent any
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }

        stage('K8s') {
            steps {
                bat 'kubectl delete deployment hello-node'
                bat 'kubectl create deployment hello-node --image=octcarp/cs304_week12'
                // bat 'kubectl set image deployments/hello-node cs304_week13_con=octcarp/cs304_week12'
            }
        }
    }
}
