node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        //sh "git config user.email hasnains312@gmail.com"
                        //sh "git config user.name hasnain393"
                        //sh "git switch master"
                        bat "cat deployment.yaml"
                        bat "sed -i 's+hasnains312/myapp.*+hasnains312/myapp:${DOCKERTAG}+g' deployment.yaml"
                        bat "cat deployment.yaml"
                        bat "git add ."
                        bat "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        bat "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main"
      }
    }
  }
}
}
