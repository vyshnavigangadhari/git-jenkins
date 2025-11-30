pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build') {
      steps {
        bat """
        if exist dist rmdir /s /q dist
        mkdir dist
        copy index.html dist\\index.html
        echo HTML_Build_OK > dist\\artifact.txt
        """
      }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: 'dist/**', allowEmptyArchive: false
    }
  }
}
