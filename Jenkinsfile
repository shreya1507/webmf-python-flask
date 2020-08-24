pipeline {
  agent { docker { image 'python:3.8' } }
  stages {
    stage('build') {
      steps {
        sh 'virtualenv venv -p python3 && source venv/bin/activate && pip install -r requirements.txt'
      }
    }
    stage('test') {
      steps {
        sh 'python test.py'
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }    
    }
  }
}
