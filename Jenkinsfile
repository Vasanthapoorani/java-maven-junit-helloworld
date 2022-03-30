pipeline {
    agent any
    tools {
        maven 'mvn'
        jdk 'jdk8'
    }
    stages {
        stage('Example') {
            steps {
                sh 'mvn --version'
            }
        }
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
                echo 'Build Success'
            }
        }        
        stage('Test') {
            steps {
                sh 'mvn test'
                echo 'Test ran successfully'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}
