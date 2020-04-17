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
          sh 'sudo -n docker build --progress=plain --build-arg JAR_FILE=build/libs/*.jar -t springio/gs-spring-boot-docker .'
          sh 'sudo -n docker run --name Demo -p 9090:9090 -p 50001:50001 -d springio/gs-spring-boot-docker'
        }
      }
    }    

    stage('Docker push to nexus repository') {
      steps {
        script {
          echo 'Running Docker push to nexus repository  ...'
          sh 'docker tag springio/gs-spring-boot-docker 172.17.0.1:8082/demo-springboot:1.0.1'
          sh 'docker login -u admin -p admin123 172.17.0.1:8082'
          sh 'docker push 172.17.0.1:8082/demo-springboot:1.0.1'
          sh 'docker logout 172.17.0.1:8081'
        }
      }
    }    
    
  }
}
