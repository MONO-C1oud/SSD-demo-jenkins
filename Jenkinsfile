flag=true

pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        // Here you can define commands for your build
      }
    }
    stage('Test') {
      steps {
        when {
          expression {
            flag == false
          }
        }        
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