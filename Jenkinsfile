pipeline {
    agent any
     tools {
        maven 'Maven' 
        }
    stages {
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("Deploy on Test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://15.206.205.23:8080/')], contextPath: '/app', war: '**/*.war'
              
            }
            
        }
        stage("Deploy on Prod"){
             input {
                message "Should we continue?"
                ok "Yes we Should"
            }
        
            
            steps{
                // deploy on container -> plugin
               eploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.110.54.207:8080/')], contextPath: '/app', war: '**/*.war'

            }
        }
    }
