pipeline {
    agent {label 'usjenkins'}
    tools {
        maven '3.8.7'
    }
    stages {
        stage('Compile') {
            steps { 
                sh 'mvn compile'
            }
        }
        stage('test') {
            steps { 
                sh 'mvn test'
            }
        }
        stage('package') {
            steps { 
                sh 'mvn package'
            }
        }
        stage('Deploy') {
            steps {
                deploy adapters: [tomcat9(url: 'http://15.206.178.231:8080/',
                            credentialsId: '0b69141a-312b-44f7-894b-68e947ea4353')],
                        war: 'target/*.war',
                        contextPath: 'AddressBook_V1'
            }
        }
    }
}
