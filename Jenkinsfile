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
      steps {
        echo 'Test some things'
        unstash 'pom-config'
        echo 'configValue'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploy some things'
      }
    }
  }
  environment {
    configValue = 'null'
  }
}