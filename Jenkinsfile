pipeline {
agent any

```
stages {

    stage('Checkout') {
        steps {
            echo 'Code checked out from GitHub'
        }
    }

    stage('Build Docker Image') {
        steps {
            sh '/usr/local/bin/docker build -t mywebsite:latest .'
        }
    }

    stage('Remove Existing Container') {
        steps {
            sh '/usr/local/bin/docker rm -f mywebsite-container || true'
        }
    }

    stage('Deploy Application') {
        steps {
            sh '/usr/local/bin/docker run -d --name mywebsite-container -p 8096:80 mywebsite:latest'
        }
    }

}

post {

    success {
        echo 'Application deployed successfully!'
    }

    failure {
        echo 'Deployment failed!'
    }

}
```

}
