pipeline {
    agent any
    triggers {
        cron('H */1 * * *')
    }
             
    tools {
        maven 'M2_HOME' 
    }
    stages {
      stage('Build'){
        steps {
          echo "Build step"
          sh 'mvn clean'
          sh 'mvn install'
          sh 'mvn package'
        }
      }
        stage('test'){
        steps {
          echo "test step"
          sh 'mvn test'
        }
      }
        stage('deploy'){
        steps {
        echo "deploy step"
        deploy adapters: [tomcat8(credentialsId: 'tomcatID', path: '', url: 'http://35.182.75.180:8080/')], contextPath: null, war: '**/*.war'
        }
      }
  }
 }
