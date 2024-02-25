pipeline {
    agent any

    stages {
        stage('Wipe Out Workspace') {
            steps {
                deleteDir()
            }
        }

        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Maven Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
}

