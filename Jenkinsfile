pipeline {
    agent any

    tools {
        jdk 'jdk21' // Configure in Manage jenkins tools use this path /usr/lib/jvm/java-21-openjdk-amd64
        maven 'M3'  // Configure in Manage jenkins tools use 3.8.8 or above
    }

    stages {

        stage('Clean Workspace') {
            steps {
                deleteDir()
            }
        }

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                url: 'https://github.com/ashishcloudops01/sample-maven-project.git'
            }
        }

        stage('Verify Tools') {
            steps {
                sh 'echo JAVA_HOME=$JAVA_HOME'
                sh 'java -version'
                sh 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }

    post {
        success {
            echo 'Build Successful ✅'
        }
        failure {
            echo 'Build Failed ❌'
        }
    }
}