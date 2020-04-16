pipeline {
  agent { node { label 'dockeragent' } }
  stages {

    stage('Prepare Stage') {
      steps {
        script {
          echo 'Running Prepare Stage ...'
        }
      }
    }

    //stage('Get Confirmation Stage') {
      //steps {
        //script {
          //input('Do you want to proceed?')
        //}
      //}
    //}

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
    
    stage('Docker build') {
      steps {
        script {
          echo 'Running Docker build stage  ...'
          //sh 'export DOCKER_BUILDKIT=1'
          sh 'sudo -s docker build --progress=plain --build-arg JAR_FILE=build/libs/*.jar -t springio/gs-spring-boot-docker .'
          //sh 'winpty sudo docker build --progress=plain --build-arg JAR_FILE=build/libs/*.jar . bash'
        }
      }
    }    


  }
}
