flag=true

pipeline {
  agent any
  parameters {
    //these are types of parameters
    string(name:'VERSION',defaultvalue:'',description:'version to deploy on prod')
    string(name:'VERSION',choices:['1.1.0','1.2.0'.'1.3.0'],description:'')
    booleanParam(name:'executeTests',defaultValue:true,description:'')
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
