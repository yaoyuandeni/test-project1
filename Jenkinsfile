pipeline {
  agent any
  stages {
    stage('Pull Code') {
      parallel {
        stage('Pull Code by web ui') {
          steps {
            sh 'echo "Pull Code by web ui"'
          }
        }

        stage('Pull Code by trigger') {
          steps {
            sh 'Pull Code by trigger'
          }
        }

      }
    }

    stage('Building and Scan') {
      parallel {
        stage('Building') {
          steps {
            container(name: 'build', shell: 'echo "build"')
          }
        }

        stage('Scan code') {
          steps {
            container(name: 'test', shell: 'echo "test"')
          }
        }

      }
    }

    stage('Build image') {
      steps {
        container(name: 'docker', shell: 'echo "build image"')
      }
    }

    stage('Deploy') {
      steps {
        container(name: 'deploy', shell: 'echo "deploy in k8s"')
      }
    }

  }
}