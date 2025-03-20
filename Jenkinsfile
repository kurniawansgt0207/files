pipeline {
  agent {
    label 'agent-jenkins-01'
  }
  
  stages {
    stage("Membuat file JSON") {
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
      }
    }
  }

}
