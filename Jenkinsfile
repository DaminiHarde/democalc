pipeline {

  agent any
  stages {
    stage('Compile') {
      steps{
        sh 'mvn clean compile'
      }
    }
    
    stage('Unit Test') {
      steps{
        sh 'mvn clean test'
      }
    }
stage('Stage1'){
steps{
 echo 'Hello Stage1' 
}
}
    stage('Package') {
      steps{
        sh 'mvn clean install'
      }
    }
stage('ConDelivery'){
steps{
deploy adapters: [tomcat9(credentialsId: '2bd4884f-047c-4af0-b688-563c0b3ffcfd', path: '', url: 'http://192.168.33.10:9090/')], contextPath: null, war: 'target/*.war'

}
}

  }
}
