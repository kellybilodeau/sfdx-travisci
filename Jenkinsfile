node {
    def HUB_ORG=env.HUB_ORG_DH
    def CONNECTED_APP_CONSUMER_KEY=env.CONNECTED_APP_CONSUMER_KEY_DH

    def sfdxLocal = tool ‘sfdx’

    stage('checkout git source') {
        checkout scm
    }

    withCredentials([file(credentialsId: ‘git-jenkins-sfdx-test’, variable: 'jwt_key_file')]) {
        stage('Authorizing') {
		    sh 'export SFDX_USE_GENERIC_UNIX_KEYCHAIN=true'
            sh '\'${sfdxLocal}/sfdx\' force:auth:jwt:grant --clientid ${CONNECTED_APP_CONSUMER_KEY} --username ${HUB_ORG} --jwtkeyfile ${jwt_key_file} --setdefaultdevhubusername -a HubOrg'
        }
    }
}