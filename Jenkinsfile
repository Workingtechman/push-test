pipeline {
  agent { label 'linux-agent' }
  parameters {
    string(name: 'PARAM_ALL_FP', defaultValue: "default 321", description: 'Parameter to write to file with git push')
  }
  stages {
    stage('push changes') {
      steps {
        echo "hello, i'm writing string parameter PARAM_ALL_FP, which is ${env.PARAM_ALL_FP} to file pushingfile.txt"
        sh 'cat "${PARAM_ALL_FP}" > pushingfile.txt && git --global user.name "Jenkins dind" && git --global user.email false@example.com && git add pushingfile.txt && git commit -a -m "made commit in pipeline" && git push'
      }
    }
  }
}

