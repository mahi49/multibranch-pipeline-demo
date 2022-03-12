pipeline {

    agent any

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '16', 
                    numToKeepStr: '10'
            )
    }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }

        stage('Code Checkout') {
            steps {
                checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'mahender', url: 'https://github.com/mahi49/multibranch-pipeline-demo.git']]]
            }
        }  

         stage(' Unit Testing') {
            steps {
                sh """
                echo "Running Unit Tests"
                """
            }
        }
         
        stage(' build') {
            steps {
                sh """
                echo "build my code"
             """  
            }
        }
       
        stage(' compile') {
            steps {
                sh """
                echo "compile my code"
             """  
            }
        }
         
         stage('package') {
            steps {
                sh """
                echo "package my war file"
                """
            }
        }
        
        stage('test') {
            steps {
                sh """
                echo "test file"
                """
            }
        }
       
        stage('Code Analysis') {
            steps {
                sh """
                echo "Running Code Analysis"
                """
            }
        }

        stage('Build Deploy Code') {
            when {
                branch 'develop'
            }
            steps {
                sh """
                echo "Building Artifact"
                """

                sh """
                echo "Deploying Code"
                """
            }
        }

    }   
}
