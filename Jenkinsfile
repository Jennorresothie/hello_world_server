pipeline {
  agent any
    stages {
      stage("CheckOut") {
        steps {
          git url: 'https://github.com/lyhan12/hello_world_server.git',
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
          sh "echo 'Docker Build'"
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
