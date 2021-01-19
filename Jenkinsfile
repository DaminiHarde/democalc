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

  }
}
