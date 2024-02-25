pipeline {
    agent {
    docker {
                    image 'maven:3.9.0'
                    args '-v /root/.m2:/root/.m2'
                    }
               }


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

