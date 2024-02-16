pipeline {
  agent any

  parameters {
    string (
      name: "Fullname",
      defaultValue: "Zulqarnain",
      description: "Enter your fullname"
    )
    choice (
      name: "ENVIRONMENT",
      choices: ["DEVELOPMENT","STAGING","PRODUCTION"],
      description: "Select an environment to deploy"
    )
  }

  stages {
    stage("Build") {
      steps {
        echo "Building...";
      }
    }
    stage("Deploy to non-production environment") {
      when {
        expression { params.ENVIRONMENT != "PRODUCTION" }
      }
      steps {
        echo "Deploying to ${params.ENVIRONMENT}.";
      }
    }
    stage("Deploy to production environment") {
      when {
        expression { params.ENVIRONMENT == "PRODUCTION" }
      }
      steps {
        input message: "Deploy to environment...", ok: "Deploy"
        echo "Deploying to ${params.ENVIRONMENT}."
      }
    }
  }
}
