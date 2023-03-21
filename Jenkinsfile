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

  }
  environment {
    registry = 'rostdocker/jenkins-task'
  }
}