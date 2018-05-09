node {
    def HUB_ORG=env.HUB_ORG_DH
    def CONNECTED_APP_CONSUMER_KEY=env.CONNECTED_APP_CONSUMER_KEY_DH

    environment {
        def SFDX_LOCAL = tool name: 'sfdx', type: 'com.cloudbees.jenkins.plugins.customtools.CustomTool'
    }

    stage('checkout git source') {
        checkout scm
    }

    withCredentials([file(credentialsId: 'git-jenkins-sfdx-test', variable: 'jwt_key_file')]) {
        stage('Authorizing') {
		    sh 'export SFDX_USE_GENERIC_UNIX_KEYCHAIN=true'
            sh '\"${SFDX_LOCAL}/sfdx\" force:auth:jwt:grant --clientid ${CONNECTED_APP_CONSUMER_KEY} --username ${HUB_ORG} --jwtkeyfile ${jwt_key_file} --setdefaultdevhubusername -a HubOrg'
        }
    }
}