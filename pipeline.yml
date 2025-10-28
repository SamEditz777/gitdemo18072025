pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build / Verify') {
      steps {
        echo "Listing repo"
        sh 'ls -la'
      }
    }

    stage('Deploy') {
      steps {
        echo "Deploying index.html to webroot"
        // overwrite the file in the mounted /var/www/html (host /opt/webroot)
        sh 'cp -f index.html /var/www/html/index.html'
      }
    }
  }

  post {
    success {
      echo "Deployed. Visit http://<EC2_PUBLIC_IP_OR_DNS> to see changes."
    }
    failure {
      echo "Build or deploy failed."
    }
  }
}
