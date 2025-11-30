pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Run Python App') {
      steps {
        bat """
        python app.py
        echo Python_Build_OK > artifact.txt
        """
      }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: 'artifact.txt', allowEmptyArchive: false
    }
  }
}
