pipeline {
  agent any
  stages {
    stage('git-checkout') {
      steps {
        script {
          checkout scm
        }

      }
    }

    stage('build') {
      steps {
        script {
          sh 'script scripts/build.sh'
        }

      }
    }

    stage('tests') {
      steps {
        script {
          sh 'script scripts/test.sh'
        }

      }
    }

    stage('docker-build') {
      steps {
        script {
          def customImage = docker.build("${registry}:${env.BUILD_ID}")
        }

      }
    }

    stage('push-image') {
      steps {
        script {
          docker.withRegistry('', 'dockerhub_id') {
            docker.image("${registry}:${env.BUILD_ID}").push('latest')
            docker.image("${registry}:${env.BUILD_ID}").push("${env.BUILD_ID}")
          }
        }

      }
    }

  }
  environment {
    registry = 'rostdocker/jenkins-task'
  }
}