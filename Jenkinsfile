pipeline {
    agent none
 
   environment {
         GITHUB_REPO = 'github.com/brandtkeller/nfs-client-provisioner.git'
    }
    options {
        skipStagesAfterUnstable()
        skipDefaultCheckout false
    }
    stages {
        stage('Build Stages') {
            agent { label 'jenkins-jenkins-agent' }
            stages {
                stage('Feature Branch') {
                    when { not { branch 'master' } }
                    steps {
                        // Helm lint at a minimum
                        sh 'echo "Stub for the feature branch build process"'
                        sh 'pwd'
                        sh 'ls -al'
                    }
                }
                stage('Master Branch') {
                    when { branch 'master' }
                    steps {
                        sh 'echo "Stub for the merge to master"'
                        sh 'pwd'
                        sh 'ls -al'
                    }
                }
                stage('Mirror to public Github') {
                    when { branch 'master' }
                        steps {
                            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                            withCredentials([usernamePassword(credentialsId: 'git_creds', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                                    sh 'git fetch --prune'
                                    sh 'git push --prune https://$GIT_USERNAME:$GIT_PASSWORD@$GITHUB_REPO +refs/remotes/origin/*:refs/heads/* +refs/tags/*:refs/tags/*'
                                }
                            }
                        }

                }
            }
        }
    }
}