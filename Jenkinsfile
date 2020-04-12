pipeline {
  agent any
  stages {

    stage('Prepare Stage') {
      steps {
        script {
          echo 'Running Prepare Stage ...'
        }
      }
    }

    stage('Get Confirmation Stage') {
      steps {
        script {
          input('Do you want to proceed?')
        }
      }
    }

    stage('Build Stage') {
      steps {
        script {
          echo 'Running Build Stage ...'
          sh './gradlew build'
        }
      }
    }

    stage('Create bootJar') {
      steps {
        script {
          echo 'Running bootRun ...'
          sh './gradlew bootJar'
        }
      }
    }

    stage('Deploy bootJar') {
      steps {
        script {
          echo 'Running bootRun ...'
          sh 'java -jar build/libs/demo-0.0.1-SNAPSHOT.jar'
        }
      }
    }    
    
    //stage('Deploy App') {
      //agent {
        //docker {
          //image 'openjdk:8-jdk-alpine'
        //}
      //}
      //steps {
        //script {
          //echo 'Running Deploy App Stage ...'
          //sh 'docker build --build-arg JAR_FILE=build/libs/*.jar -t springio/gs-spring-boot-docker .'
        //}
      //}
    //}    
    
  }
}
