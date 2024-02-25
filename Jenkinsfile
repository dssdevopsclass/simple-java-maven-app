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

        stage('Code Scan') {
            when {
                environment name: 'RUN_SONAR', value: 'true'
            }
            steps {
                sh 'mvn sonar:sonar'
            }
        }

        stage('Checkmarx Scan') {
            when {
                environment name: 'RUN_CHECKMARX', value: 'true'
            }
            steps {
                sh 'checkmarx_scan_command_here'
            }
        }

        stage('Deploy WAR') {
            when {
                environment name: 'DEPLOY_WAR', value: 'true'
            }
            steps {
                sh 'deliver.sh'
            }
        }

        stage('Deploy Properties') {
            when {
                environment name: 'DEPLOY_PROPERTIES', value: 'true'
            }
            steps {
                sh 'deliver.sh'
            }
        }
    }
}

