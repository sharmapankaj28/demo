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

    stage('Deploy Stage') {
      steps {
        script {
          echo 'Running bootRun ...'
          sh './gradlew bootJar'
        }
      }
    }

  }
}
