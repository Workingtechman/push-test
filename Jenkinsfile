pipeline {
  agent { label 'linux-agent' }
  parameters {
    string(name: 'PARAM_ALL_FP', defaultValue: "default 321", description: 'Parameter to write to file with git push')
  }
  stages {
    stage('push changes') {
      steps {
        withCredentials([gitUsernamePassword(credentialsId: 'github_jenkins_push_username_token', gitToolName: 'Default')]) {
          echo "hello, i'm writing string parameter PARAM_ALL_FP, which is \"${env.PARAM_ALL_FP}\" to file pushingfile.txt"
          sh 'git status && HASH_COMMIT=$(git rev-parse HEAD) && echo "Hash of the current branch is ${HASH_COMMIT}" && echo "${PARAM_ALL_FP}" > pushingfile.txt && git config --global user.name "Jenkins dind" && git config --global user.email false@example.com && git add pushingfile.txt && git commit -a -m "made commit in pipeline" && git push origin HEAD:master'
        }
      }
    }
  }
}

