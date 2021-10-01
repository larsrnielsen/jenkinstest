// node {
//     withCredentials([[$class: 'VaultTokenCredentialBinding', credentialsId: 'jenkins', vaultAddr: 'http://localhost:8200']]) {
//         // values will be masked
//         sh 'echo TOKEN=$VAULT_TOKEN'
//         sh 'echo ADDR=$VAULT_ADDR'
//     }
// }

node {    
    def secrets = [
        [path: 'secret/foo', engineVersion: 2, secretValues: [
            [vaultKey: 'bar', envVar: 'BAR']]]
    ]
    def configuration = [vaultUrl: 'http://localhost:8200',
                         vaultCredentialId: 'jenkins',
                         engineVersion: 2]

    pipeline {
        agent any
        options {
            buildDiscarder(logRotator(numToKeepStr: '20'))
            disableConcurrentBuilds()
        }
        stages{
            stage('Vault') {
                steps {
                    withVault([configuration: configuration, vaultSecrets: secrets]) {
                        sh "echo hello"
                        sh "echo ${env.BAR}"
                    }

                }
            }
        }
    }

    // stage('Compile') { // Compile and do unit testing
    //    // run Gradle to execute compile and unit testing
    //    sh "echo compile"
    //    withCredentials([[$class: 'VaultTokenCredentialBinding', credentialsId: 'jenkins', vaultAddr: 'http://localhost:8200']]) {
    //     // values will be masked
    //     sh 'echo TOKEN=$VAULT_TOKEN'
    //     sh 'echo ADDR=$VAULT_ADDR'
    //   }
      
    //   withVault([configuration: configuration, vaultSecrets: secrets]) {
    //     sh 'echo $bar'
    //     sh 'echo $env'
    //     sh 'echo $env.bar'
    //     sh 'printenv'
    // }
    // }
}

// node {
//     // define the secrets and the env variables
//     // engine version can be defined on secret, job, folder or global.
//     // the default is engine version 2 unless otherwise specified globally.
//     def secrets = [
//         [path: 'secret/foo', engineVersion: 2, secretValues: [
//             [vaultKey: 'bar']]]
//     ]

//     stage('Compile') { // Compile and do unit testing
//        // run Gradle to execute compile and unit testing
//        sh "echo DDDDDDDDDDDDDDDDDDD"
//     }
    
//     // inside this block your credentials will be available as env variables
//     withVault([configuration: configuration, vaultSecrets: secrets]) {
//         sh 'echo xyz'
//         sh 'echo $bar'
//     }
   
//    sh 'echo ABCxxxxxx'
    
//    withCredentials([[$class: 'VaultTokenCredentialBinding', credentialsId: 'jenkins', vaultAddr: 'http://localhost:8200']]) {
//         // values will be masked
//         sh 'echo TOKEN=$VAULT_TOKEN'
//         sh 'echo ADDR=$VAULT_ADDR'
//     }
// }
