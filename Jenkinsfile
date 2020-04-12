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

    stage('Deploy App') {
      steps {
        script {
          echo 'Running Deploy App Stage ...'
          sh 'docker build --build-arg JAR_FILE=build/libs/*.jar -t springio/gs-spring-boot-docker .'
        }
      }
    }    
    
  }
}
