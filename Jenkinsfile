pipeline {
  agent any
  stages {
    stage('Update dockerfile') {
      steps {
      script {
        catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'cred_token', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')])  {
                        
                        sh "git config user.email sokphakphol@gmail.com"
                        sh "git config user.name PholSoophak"
                        sh "sed -i \"s+sophak12/devops_spring.*+sophak12/devops_spring:${DOCKERTAG}+g\" app/deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/Manifest_deploy_spring_jenkins_argocd.git HEAD:main"
          
        }
      }
      }
  }
}
}
}