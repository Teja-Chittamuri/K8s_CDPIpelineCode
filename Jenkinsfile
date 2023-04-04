
pipeline {
 ageny any
  stages{
    stage('Fetch the code')
    {
        steps{
            git branch:'master' , url:'https://github.com/Teja-Chittamuri/K8s_CDPIpelineCode-.git'
        }
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'githublogin', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email Tejschittamuri@gmail.com"
                        sh "git config user.name TejaChittamuri"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+tejachittamuri/cicd.*+tejachittamuri/cicd:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job updatemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/K8s_CDPIpelineCode.git HEAD:master"
      }
    }
  }
}
  }
}
