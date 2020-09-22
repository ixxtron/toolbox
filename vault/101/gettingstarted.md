# Getting Started with Vault

# Dev Mode
### 'Dev' server is a built-in, pre-configured server
- useful for local development, testing, and exploration
- everything is stored in memory
- here vault is automatically unsealed
- and not very secure
### DO NOT runt a DEV server in production!!

## Starting my Vault Server

### 1. Start vault server
`vault server -dev`

### 2. Open new shell and run the following commands...
- copy and run the export the VAULT_ADDR command
` $ export VAULT_ADDR='http://127.0.0.1:8200' `
* This will configure my vault client to talk to the vault server *

### 3. Save the unseal key somewhere
` echo "7QPvOvkhjhhEOQi6XuM0/n8SsLAJ+07MDWIrW1mx5+Mz8=" > unseal.key `

### 4. Repeat step 2  but with root token
` export VAULT_DEV_ROOT_TOKEN_ID=s.ycMfPe5vkBygDaoimNDCjrc2 `

### 5. Very the server is running by running the Vault status command
` vault status `

> Key             Value
---             -----
Seal Type       shamir
Initialized     true
Sealed          false
Total Shares    1
Threshold       1
Version         1.5.3
Cluster Name    vault-cluster-36f83d82
Cluster ID      f12c75d1-2396-e78a-3b1e-7a97e522b7d6
HA Enabled      false

