pipeline {
    agent {
      label 'slave'
    }
    tools {
        maven 'M2_HOME'
    }
    stages {
        stage('checkout the project') {
            steps {
                git branch: 'master', url: 'https://github.com/mjjawad/addressbook.git'
            }
        }
        stage('Build the Package') {
            steps {
                sh'mvn test'
            }
        }
        stage('Deploy on  Slaves') {
            steps {
              deploy adapters: [tomcat9(credentialsId: 'a0c0dff3-2d41-4ce2-86d9-adba602419b2', path: '', url: 'http://52.66.243.44:8081/')], contextPath: null, onFailure: false, war: '**/*.war'
            }        
            
        }
    }
}
