node {
    withCredentials([[$class: 'VaultTokenCredentialBinding', credentialsId: 'jenkins', vaultAddr: 'https://localhost:8200']]) {
        // values will be masked
        sh 'echo TOKEN=$VAULT_TOKEN'
        sh 'echo ADDR=$VAULT_ADDR'
    }
}
