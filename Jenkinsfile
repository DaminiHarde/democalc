pipeline {

  agent any
environment {
 imagename = "daminiharde/calculator:v$BUILD_NUMBER"
 registryCredential = 'docker'
 dockerImage = ''
 }

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

stage ('Building image') {
 steps {
 script {
 dockerImage = docker.build imagename
 }
 }
 }
 stage ('Running Container') {
 steps {
 script {
 sh 'docker rm --force tomcat9999 && echo 1'
 dockerImage.run('--name tomcat9999 -p 9999:8080')
 }
 }
 }
 stage ('Push Image') {
 steps {
 script {
 docker.withRegistry( '', registryCredential ) {
 dockerImage.push()
 }
 }
 }
 }

  }
}
