#!groovy

pipeline {

  agent {
    label "docker"
  }

  options {
    skipDefaultCheckout()
  }

  environment {
    TERRAFORM_VERSION="${params.TERRAFORM_VERSION}"
  }

  parameters {
    string(
      name: "TERRAFORM_VERSION",
      defaultValue: "0.11.13",
      name: "TERRAFORM_VERSION"
    )
  }

  stages {

    stage("Test") {
      steps {
        echo "${TERRAFORM_VERSION}"
      }
    }
  }
  post {
    always {
      deleteDir()
    }
  }
}
