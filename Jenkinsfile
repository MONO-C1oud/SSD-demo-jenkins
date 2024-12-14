flag=true

pipeline {
  agent any
  tools {
    maven 'Maven'
  }
  environment {
    //variables defined here can be used at any stage
    NEW_VERSION='1.0.0'
  }
  stages {
    stage('Build') {
      steps {
        echo 'Building Project...'
        echo "Building version ${NEW_VERSION}"
        // Here you can define commands for your build
        bat "nvm install"
      }
    }
    stage('Test') {
      when {
        expression {
          flag == false
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
        // Here you can define commands for your deployment
      }
    }
  }
  post {
    // The condition here will execute after the build is done
    always {
      // This action will happen always regardless of the result of the build
      echo 'Post build condition running'
    }
    failure {
      // This action will happen only if the build has failed
      echo 'Post action if build failed'
    }
  }
}
