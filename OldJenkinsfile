pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar'
            }
        }   
      stage('Unit Test - Junit and Jacoco Added Tests') {
        steps {
          sh "mvn test" 
          }
           post {
            always {
              junit 'target/sunfire-reports/*.xml'
              jacoco execPattern: 'target/jacoco.exec'
            }
           }
      }
  }
}