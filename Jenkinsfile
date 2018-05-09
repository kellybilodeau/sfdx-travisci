// pipeline {

//     agent any

//     environment {
//         HUB_ORG="${env.HUB_ORG_DH}"
//         CONNECTED_APP_CONSUMER_KEY="${env.CONNECTED_APP_CONSUMER_KEY_DH}"
//     }

//     withCredentials([file(credentialsId: 'git-jenkins-sfdx-test', variable: 'jwt_key_file')]) {
//         stages {
//             stage('AUTHORIZING') {
//                 steps {
//                     sh '''
//                         echo $HUB_ORG
//                         echo $CONNECTED_APP_CONSUMER_KEY
//                         export SFDX_USE_GENERIC_UNIX_KEYCHAIN=true'
//                         /usr/local/lib/sfdx/bin/sfdx force:auth:jwt:grant --clientid ${CONNECTED_APP_CONSUMER_KEY} --username ${HUB_ORG} --jwtkeyfile ${jwt_key_file} --setdefaultdevhubusername -a HubOrg
//                     '''
//                 }
//             }
//         }
//     }
// }

// pipeline {

//     agent any

// environment {
//     HUB_ORG="${env.HUB_ORG_DH}"
//     CONNECTED_APP_CONSUMER_KEY="${env.CONNECTED_APP_CONSUMER_KEY_DH}"
// }

// stage('deploy') {
//     steps {
//         withCredentials([
//                 file(credentialsId: 'git-jenkins-sfdx-test', 
//                 variable: 'jwt_key_file'
//             )]) {
//             sh '''
//                 echo $HUB_ORG
//                 echo $CONNECTED_APP_CONSUMER_KEY
//                 export SFDX_USE_GENERIC_UNIX_KEYCHAIN=true'
//                 /usr/local/lib/sfdx/bin/sfdx force:auth:jwt:grant --clientid ${CONNECTED_APP_CONSUMER_KEY} --username ${HUB_ORG} --jwtkeyfile ${jwt_key_file} --setdefaultdevhubusername -a HubOrg
//             ''' }
//     }
// }
// }

// pipeline {
//   agent any
//   stages {
//     withCredentials([file(credentialsId: 'git-jenkins-sfdx-test', variable: 'jwt_key_file')]) {
//     stage('authorizing') {
//       environment {
//         HUB_ORG="${env.HUB_ORG_DH}"
//         CONNECTED_APP_CONSUMER_KEY="${env.CONNECTED_APP_CONSUMER_KEY_DH}"
//       }
//       steps {
//             sh '''
//                 echo $HUB_ORG
//                 echo $CONNECTED_APP_CONSUMER_KEY
//                 export SFDX_USE_GENERIC_UNIX_KEYCHAIN=true'
//                 /usr/local/lib/sfdx/bin/sfdx force:auth:jwt:grant --clientid ${CONNECTED_APP_CONSUMER_KEY} --username ${HUB_ORG} --jwtkeyfile ${jwt_key_file} --setdefaultdevhubusername -a HubOrg
//             '''
//       }
//     }
//   }
//   }
// }


#!groovy
node {
    environment {
        HUB_ORG="${env.HUB_ORG_DH}"
        CONNECTED_APP_CONSUMER_KEY="${env.CONNECTED_APP_CONSUMER_KEY_DH}"
    }

    stage('checkout git source') {
        checkout scm
    }

    withCredentials([file(credentialsId: 'git-jenkins-sfdx-test', variable: 'jwt_key_file')]) {
        stage('Authorizing') {
		    sh '''
                echo $HUB_ORG
                echo $CONNECTED_APP_CONSUMER_KEY
                export SFDX_USE_GENERIC_UNIX_KEYCHAIN=true'
                /usr/local/lib/sfdx/bin/sfdx force:auth:jwt:grant --clientid ${CONNECTED_APP_CONSUMER_KEY} --username ${HUB_ORG} --jwtkeyfile ${jwt_key_file} --setdefaultdevhubusername -a HubOrg
            '''
         }
    }
}

                // export SFDX_USE_GENERIC_UNIX_KEYCHAIN=true'
                // /usr/local/lib/sfdx/bin/sfdx force:auth:jwt:grant --clientid ${CONNECTED_APP_CONSUMER_KEY} --username ${HUB_ORG} --jwtkeyfile ${jwt_key_file} --setdefaultdevhubusername -a HubOrg
       