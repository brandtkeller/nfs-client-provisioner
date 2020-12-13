pipeline {
    agent none
 
   environment {
         GITHUB_REPO = 'https://github.com/brandtkeller/nfs-client-provisioner.git'
    }
    options {
        skipStagesAfterUnstable()
        skipDefaultCheckout false
    }
    stages {
        stage('Development Build') {
            agent any
            when { not { branch 'master' } }
            steps {
                // Helm lint at a minimum
                sh 'echo "Stub for the feature branch build process"'
                sh 'pwd'
                sh 'ls -al'
            }
        }

        stage('Master Build') {
            agent any
            when { branch 'master' }
            steps {
                sh 'echo "Stub for the merge to master"'
                sh 'pwd'
                sh 'ls -al'
            }
        }

    //     stage('Mirror to public Github') {
    //         agent any
    //         when { branch 'master' }
    //         steps {
    //             catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
    //             withCredentials([usernamePassword(credentialsId: 'git_creds', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
    //                             sh 'rm -rf *'
    //                             sh 'git clone --mirror $HOME_REPO'
    //             }
    //             withCredentials([usernamePassword(credentialsId: 'github_creds', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
    //                         dir("${PROJECT}.git"){
    //                                 sh 'git remote add --mirror=fetch github https://$GIT_USERNAME:$GIT_PASSWORD@$GITHUB_REPO'
    //                                 sh 'git push github --all'
    //                         }
    //                 }
    //             }
    //         }
    //   }
    }
}