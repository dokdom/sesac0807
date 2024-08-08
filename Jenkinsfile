pipeline { 
  agent any 
  triggers { 
    pollSCM('* * * * *') 
  } 
  stages { 
    stage('Checkout') { 
      steps { 
        git branch: 'main',  
        url: 'https://github.com/dokdom/sesac0807.git' 
      } 
    } 
    stage('Build') { 
      steps { 
        sh 'mvn clean package' 
      } 
    } 
    stage('Test') { 
      steps { 
        echo 'This is Jenkinsfile'
        sh 'mvn --version' 
      } 
    } 
    stage('Deploy') { 
      steps { 
        deploy adapters: [tomcat9(credentialsId: 'admin', url: 'http://192.168.56.102:8080/')], contextPath: null, war: 'path/to/war' 
      } 
    } 
  } 
} 