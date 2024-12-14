flag = true

pipeline {
  agent any
  parameters {
    // Fixed parameter syntax
    string(name: 'VERSION', defaultValue: '', description: 'Version to deploy on prod')
    choice(name: 'VERSION_CHOICES', choices: ['1.1.0', '1.2.0', '1.3.0'], description: 'Select version')
    booleanParam(name: 'executeTests', defaultValue: true, description: 'Execute tests?')
  }
  environment {
    // Variables defined here can be used at any stage
    NEW_VERSION = '1.0.0'
  }
  stages {
    stage('Build') {
      steps {
        echo 'Building Project...'
        echo "Building version ${NEW_VERSION}"
        // Here you can define commands for your build
      }
    }
    stage('Test') {
      when {
        expression {
          params.executeTests
        }
      }
      steps {
        echo 'Testing..'
        // Here you can define commands for your tests
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploying....'
        echo "Deploying version ${params.VERSION}"
        // Here you can define commands for your deployment
      }
    }
  }
  post {
    // The condition here will execute after the build is done
    always {
      echo 'Post build condition running'
    }
    failure {
      echo 'Post action if build failed'
    }
  }
}
