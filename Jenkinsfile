pipeline {
   
   tools {
        maven 'Maven3'
    }
    agent any
    stages {
        stage('Cloning Git') {
            steps {
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/AbdulShukur007/Ansible-demo.git']]])
            }
        }  
        stage('Maven Build'){
            steps {
                sh 'mvn clean install'           
            }
        }
        stage('Artificats Upload'){
           steps {
              nexusArtifactUploader artifacts: [[artifactId: 'LoginWebApp', classifier: '', file: 'artifactPath', type: 'war'], [artifactId: 'LoginWebApp', classifier: '', file: 'pom.xml', type: 'pom']], credentialsId: 'nexus', groupId: 'com.devops4solutions', nexusUrl: '44.203.200.106:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'http://44.203.200.106:8081/repository/maven-releases/', version: '1'
           }
        }   
    }
 }
