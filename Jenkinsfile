pipeline {
  agent none
  
  stages {
    stage("Membuat file JSON") {
      agent {
        label 'agent-jenkins-01'
      }
      steps {
        echo "Mulai membuat file JSON"
        script {
          def JsonData = [
              pipelineStart: new Date().toString(),
              buildStatus: 'success',
              buildTime: new Date().toString(),
              deployTime: new Date().toString(),
            ]

            writeJSON file: '/var/lib/jenkins/workspace/Pipeline-Utility-Step/info.json', json: JsonData
            echo "Json data berhasil di buat pada /var/lib/jenkins/workspace/Pipeline-Utility-Step"
        }
        echo "Selesai membuat file JSON"
      }
    }

    stage("Membaca file JSON") {
      agent {
        label 'agent-jenkins-02'
      }
      steps {
        echo "Mulai membaca file info.json"
        script {
          def JsonContent = sh(script: 'cat /var/lib/jenkins/workspace/Pipeline-Utility-Step/info.json', returnStdout: true).trim()
          def buildStatus = sh(script: 'cat /var/lib/jenkins/workspace/Pipeline-Utility-Step/info.json | jq .buildStatus', returnStdout: true).trim()
          def deployTime = sh(script: 'cat /var/lib/jenkins/workspace/Pipeline-Utility-Step/info.json | jq .deployTime', returnStdout: true).trim()
          echo "JSON Content: \n${JsonContent}"
          echo "buil status: \n${buildStatus}"
          echo "deploy time: \n${deployTime}"
        }
        echo "Selesai membaca file info.json"
      }
    }
  }

}
