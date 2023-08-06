node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        //sh "git config user.email hasnains312@gmail.com"
                        //sh "git config user.name hasnain393"
                        //sh "git switch master"
                        //sh "cat deployment.yaml"
                        //sh "sed -i 's+hasnains312/myapp.*+hasnains312/myapp:${DOCKERTAG}+g' deployment.yaml"
                        //sh "cat deployment.yaml"
                        //sh "git add ."
                        //sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        //sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main"

                        def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        bat 'git config user.email hasnains312@gmail.com'
                        bat 'git config user.name hasnain393'
                        bat 'git switch master'
                        bat "type deployment.yaml"
                        bat "powershell -Command \"(Get-Content deployment.yaml) -replace 'hasnains312/myapp.*', 'hasnains312/myapp:${DOCKERTAG}' | Set-Content deployment.yaml\""
                        bat "type deployment.yaml"
                        bat "git add ."
                        bat "git commit -m \"Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}\""
                        bat "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main"
        }
      }
    }
  }
}
}
