pipeline {
  agent any
  environment {
    // The following variable is required for a Semgrep Cloud Platform-connected scan:
    SEMGREP_APP_TOKEN = credentials('SEMGREP_APP_TOKEN')
    SEMGREP_REPO_NAME = "from-jenkins/railsgoat"
  }
  
  stages {
        stage('Semgrep-Scan') {
          steps {
              sh '''docker pull returntocorp/semgrep && \
              docker run \
              -e SEMGREP_APP_TOKEN=$SEMGREP_APP_TOKEN \
              -e SEMGREP_REPO_NAME=$SEMGREP_REPO_NAME \
              -v "$(pwd):$(pwd)" --workdir $(pwd) \
              returntocorp/semgrep semgrep ci '''
        }
      }
    }
}
