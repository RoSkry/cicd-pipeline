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

  }
  environment {
    registry = 'rostdocker/jenkins-task'
  }
}