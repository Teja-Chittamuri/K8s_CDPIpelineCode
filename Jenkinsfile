node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }
    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'githublogin', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email tejschittamuri@gmail.com"
                        sh "git config user.name TejaChittamuri"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+tejachittamuri/ultimatecicd.*+tejachittamuri/ultimatecicd:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/K8s_CDPIpelineCode.git HEAD:master"
      }
    }
  }
}
}
