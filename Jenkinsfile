pipeline{
    agent any
    tools {
        maven "maven" //this is the name you gave in configuration for maven in global tool configuration!
    }
    stages{
        stage("Test"){
            steps{
                sh 'mvn test'
            }
        }
        stage("Build"){
            steps{
                sh 'mvn package'
            }
        }
        stage("Deploy to Test"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat-creds', path: '', url: 'http://192.168.1.128:8083')], contextPath: null, onFailure: false, war: '**/*.war'
            }
        }
    }
}
