pipeline {
  agent { label 'linux-agent' }
  parameters {
    string(name: 'PARAM_ALL_FP', defaultValue: "e82867e9c5c4981c6a274ed97f2a4d6a5901586d", description: 'Parameter to write to file with git push')
  }
  stages {
    stage('push changes') {
      steps {
        withCredentials([gitUsernamePassword(credentialsId: 'github_jenkins_push_username_token', gitToolName: 'Default')]) {
          echo "hello, i'm writing string parameter PARAM_ALL_FP, which is \"${env.PARAM_ALL_FP}\" to file pushingfile.txt"
          sh 'git status && HASH_COMMIT=$(git rev-parse HEAD) && echo "Hash of the current branch is ${HASH_COMMIT}" &&  echo "previous commit is ${params.PARAM_ALL_FP}" && git --no-pager diff ${params.PARAM_ALL_FP}..${HASH_COMMIT} && echo "sleep 30 sec" && sleep 30 && echo "${PARAM_ALL_FP}" > pushingfile.txt && git config --global user.name "Jenkins dind" && git config --global user.email false@example.com && git add pushingfile.txt && git commit -a -m "made commit in pipeline" && git push origin HEAD:master'
        }
      }
    }
  }
}

