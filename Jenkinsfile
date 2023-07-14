pipeline {
  agent any
  environment {
    GITHUB_REPO="https://github.com/Jennorresothie/hello_world_server"
    DOCKER_REPO="conna/hello_world_server"
    VERSION=1.0
  }
    stages {
      stage("CheckOut") {
        steps {
          git url: "$GITHUB_REPO",
              branch: 'main'
        }
      }
      stage("Code Build") {
        steps {
          sh "echo 'Code Build'"
        }
      }
      stage("Unit Test") {
        steps {
          sh "echo 'Unit Test'"
        }
      }
      stage("Docker Build") {
        steps {
          sh "docker build -t $DOCKER_REPO:$VERSION ."
        }
      }
      stage("Docker Push") {
        steps {
          sh "echo 'Docker Push'"
        }
      }
      stage("Deploy") {
        steps {
          sh "echo 'Deploy'"
        }
      }

    }
  post {
        success {
            slackSend (
                channel: "U04QDGSJSUV",
                color: "#00FF00",
                message: "SUCCESS : Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]"
            )
        }
        failure {
            slackSend (
                channel: "U04QDGSJSUV",
                color: "#FF0000",
                message: "FAIL : Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]"
            )
        }
    }
  }
