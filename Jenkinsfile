pipeline {
  agent any
  stages {
    stage('build') {
      parallel {
        stage('build') {
          agent any
          environment {
            VAR1 = '100'
          }
          steps {
            sh 'sleep ${ENV1}'
          }
        }
        stage('build2') {
          steps {
            sh 'echo \'done\''
          }
        }
      }
    }
    stage('test') {
      steps {
        echo 'testing'
        sleep 10
      }
    }
    stage('3rstage') {
      steps {
        sleep 1
        build(job: 'job1', propagate: true, wait: true, quietPeriod: 10)
      }
    }
  }
  environment {
    ENV1 = '10'
  }
}