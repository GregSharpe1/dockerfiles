#!groovy

pipeline {

  agent {
    label any 
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
      description: "Terraform version you wish to build within a container."
    )
  }

  stages {

    stage("Checkout SCM") {
      steps {
        checkout scm
      }
    }

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
