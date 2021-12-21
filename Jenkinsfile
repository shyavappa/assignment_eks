// Git Variables
def gitRepoName = "https://github.com/lRAHULl/rahul-eks.git"
def gitBranch = "master"

// Triggers
properties([pipelineTriggers([githubPush()])])

// Pipeline script
pipeline {
    // Agents
    agent any

    // Stages In the pipeline
    stages {
        // Checkout from the Source Control
        stage('Checkout') {
            steps {
              echo "====++++ Checkout ++++===="
              git branch: "${gitBranch}", url: "${gitRepoName}"
              echo "====++++ Checkout Successful ++++===="
            }
        }

        stage('Init') {
            steps {
              echo "====++++ Init ++++===="
              sh "terraform init"
              echo "====++++ Init Successful ++++===="
            }
        }

        stage('Validate') {
            steps {
              echo "====++++ Validate ++++===="
              sh "terraform validate"
              echo "====++++ Validate Successful ++++===="
            }
        }

        stage('Dev') {
            steps {
              echo "====++++ Deploy to Dev ++++===="
              sh "terraform plan"
              sh "terraform plan -destroy"
              input "Review the Terraform plan above"
              // sh "terraform apply --auto-approve"
              sh "terraform destroy --auto-approve"
              echo "====++++ Deploy to Dev Successful ++++===="
            }
        }

        stage('QA') {
            steps {
              echo "====++++ Deploy to QA ++++===="
              echo "====++++ Deploy to QA Skipped ++++===="
            }
        }

        stage('Stage') {
            steps {
              echo "====++++ Deploy to Stage ++++===="
              echo "====++++ Deploy to Stage Skipped ++++===="
            }
        }

        stage('Prod') {
            steps {
              echo "====++++ Deploy to Prod ++++===="
              echo "====++++ Deploy to Prod Skipped ++++===="
            }
        }
    }
}
