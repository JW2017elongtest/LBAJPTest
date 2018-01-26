pipeline {
  agent {
    node {
      label 'docker'
    }
    
  }
  stages {
    stage('Build') {
      steps {
        echo 'Hello from Build'
        writeFile(file: 'config', text: 'version=1', encoding: 'UTF-8')
        stash(name: 'pom-config', includes: 'config')
      }
    }
    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'Test some things'
            unstash 'pom-config'
            readFile(encoding: 'UTF-8', file: 'config')
            echo 'configValue'
          }
        }
        stage('supertest') {
          steps {
            sleep 2
            echo 'winning'
          }
        }
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploy some things'
        input 'Do you want to deploy?'
        echo 'deployed'
      }
    }
  }
  environment {
    configValue = null
  }
}