#!groovy
node {
    def HUB_ORG=env.HUB_ORG_DH
    def CONNECTED_APP_CONSUMER_KEY=env.CONNECTED_APP_CONSUMER_KEY_DH

    def SFDX_LOCAL = tool 'sfdx'

    stage('checkout git source') {
        checkout scm
    }

    withCredentials([file(credentialsId: 'git-jenkins-sfdx-test', variable: 'jwt_key_file')]) {
        stage('Authorizing') {
		    sh 'export SFDX_USE_GENERIC_UNIX_KEYCHAIN=true'
            sh '/usr/local/lib/sfdx/bin/sfdx force:auth:jwt:grant --clientid 3MVG9zlTNB8o8BA3oXqMc8JyzW47tEEqPUxh3XsUdxzOLzP_xlEssf983JZImNj9VS5h5_SQMlth6lyo_k.d4 --username kbils@oreo.com --jwtkeyfile ${jwt_key_file} --setdefaultdevhubusername -a HubOrg'
        }
    }
}