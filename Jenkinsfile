#!groovy

def branch = (env.CHANGE_ID) ? env.CHANGE_BRANCH : env.BRANCH_NAME;
def changes = []
def whatToBuild = []
def gitHash

pipeline {

  options {
    disableConcurrentBuilds()
    ansiColor('xterm')
    buildDiscarder(
      logRotator(
        daysToKeepStr: '365',
        artifactDaysToKeepStr: '365'
      )
    )
  }

  agent any

  stages{

    stage('Checkout') {
      steps {
        deleteDir()
        checkout scm
      }
    }

    stage ('Discovering Changes') {
      steps {
        script {

          gitHash = sh ( returnStdout: true, script: 'git rev-parse --short HEAD' ).trim()
          def changeLogSets = currentBuild.rawBuild.changeSets

          for (int i = 0; i < changeLogSets.size(); i++) {
            def entries = changeLogSets[i].items
            for (int j = 0; j < entries.length; j++) {
              def entry = entries[j]
              def files = new ArrayList(entry.affectedFiles)
              for (int k = 0; k < files.size(); k++) {
                def file = files[k]
                def path = file.getPath()
                // As the directory structure is {CONTAINER_NAME}/Dockerfile
                // Let's extract just the path to the Dockerfile and use later
                if (path.contains("/")){
                  path = path.split("/")[0]
                  changes.push(path)
                }
              }
            }
          }
        }
      }
    }

    stage('Verify changes') {
      steps {
        script {
          changes.each {
            if (!fileExists("${it}/Dockerfile")) {
              return
            } else {
              whatToBuild.push(it)
            }
          }
        }
      }
    }

    stage('Build Container(s)') {
      steps {
        script {
          if (whatToBuild.size() == 0) {
            echo "LOG: No container to build."
            return
          } else {
            whatToBuild.each{
              docker.build("gregsharpe/${it}:latest", "-f ${it}/Dockerfile ${it}")
            }
          }
        }
      }
    }

    stage('Push Container(s)') {
      // when {
      //   branch 'master'
      // }
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'gregsharpe-dockerhub') {
            whatToBuild.each{
              sh "docker push gregsharpe/${it}:latest"
            }
          }
        }
      }
    }
  }

  // Make sure to remove all Docker containers built within this pipeline
  post {
    always {
      script {
        whatToBuild.each{
          sh "docker rmi --force ${it}:latest"
        }
      }
    }
  }

}
