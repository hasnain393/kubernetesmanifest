node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Update GIT') {
        catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
            withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                bat 'git config user.email hasnains312@gmail.com'
                bat 'git config user.name Hasnain'
                // You may need to use 'git switch master' or equivalent Git command here.
                // However, the "git switch" command is not available by default in older Git versions. You can use 'git checkout' instead.

                // The sed command should be replaced with PowerShell for Windows.
                bat 'type deployment.yaml'
                bat "powershell -Command \"(Get-Content deployment.yaml) -replace 'hasnains312/myapp.*', 'hasnains312/myapp:${DOCKERTAG}' | Set-Content deployment.yaml\""
                bat 'type deployment.yaml'

                bat 'git add .'
                bat "git commit -m \"Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}\""
                bat "git remote add origin https://github.com/hasnain393/kubernetesmanifest.git"
                bat "git push  https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main"
            }
        }
    }
}
