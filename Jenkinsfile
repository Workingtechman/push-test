pipeline {
  agent { label 'linux-agent' }
  parameters {
    string(name: 'PARAM_ALL_FP', defaultValue: "default 321", description: 'Parameter to write to file with git push')
  }
  stages {
    stage('push changes') {
      steps {
        withCredentials([string(credentialsId: 'github_jenkins_push_token', variable: 'TOKEN')]) {
          echo "hello, i'm writing string parameter PARAM_ALL_FP, which is \"${env.PARAM_ALL_FP}\" to file pushingfile.txt"
          sh 'git status && echo "${PARAM_ALL_FP}" > pushingfile.txt && git config --global user.name "Jenkins dind" && git config --global user.email false@example.com && git add pushingfile.txt && git commit -a -m "made commit in pipeline" && git push origin HEAD:master'
        }
      }
    }
  }
}

