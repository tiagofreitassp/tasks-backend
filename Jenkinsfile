pipeline {
    agent any
    stages {
        stage ('Build Backend'){
            steps {
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage ('Unit Tests'){
            steps {
                sh 'mvn test'
            }
        }
        stage ('Deploy Backend') {
            deploy adapters: [tomcat8(credentialsId: 'TomcatLogin', path: '', url: 'http://localhost:8001/')], contextPath: 'tasks-backend', war: 'target/tasks-backend.war'
        }
    }
}