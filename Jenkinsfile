node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([gitUsernamePassword(credentialsId: '2e870c5a-54bb-4f34-94a1-586d17a32b58', gitToolName: 'LocalGIT')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email rajtiwari10091995@gmail.com"
                        sh "git config user.name RajDevO"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+kuberaj/project_001.*+kuberaj/project_001:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/m_project_001_manifest.git HEAD:main"
      }
    }
  }
}
}
