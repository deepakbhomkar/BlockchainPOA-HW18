# BlockchainPOA-HW18

# ZBANK Testnet Blockchain - Proof of authority

# How to use testnet blockchain `zbank` to transfer crypto between two nodes


### The Proof of Authority (PoA) algorithm is typically used for private blockchain networks as it requires pre-approval of, or voting in of, the account addresses that can approve transactions (seal blocks).

## Nodes created within the genesis block `zbank` with addresses
*   zbanknode1
    *   0xFb560e9951D07E27925F1b2F1bc3bD58E734fe47
*   zbanknode2
    *   0x64C76D13c24334C44f762251a9a9e5AE9CAa1cCD
*   These are linked together by chain id `3434`

## How to start mining blocks using the above information

##  Step 1
* Run the following geth command in one terminal window:
    * ./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock
    * ./geth --datadir zbanknode1 --unlock "0xFb560e9951D07E27925F1b2F1bc3bD58E734fe47" --mine --rpc --allow-insecure-unlock
    
    * **NOTE:** Type your password and hit enter - even if you can't see it visually!
    
    * Get enode address from the logs above by scrollinh u pand searching for enode
        * self=enode://535346540290b9c1071f7babcc35432a60e5aa5eeb470e96f848fb1e0fe95866ded0743d04f1068403235243eae231c6145ca20f7a93ae497600529ece135823@127.0.0.1:30303 

## Step 2
* Run the following geth command in a different terminal window:
    * ./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock

    * ./geth --datadir zbanknode2 --unlock "0x64C76D13c24334C44f762251a9a9e5AE9CAa1cCD" --mine --port 30304 --bootnodes "enode://535346540290b9c1071f7babcc35432a60e5aa5eeb470e96f848fb1e0fe95866ded0743d04f1068403235243eae231c6145ca20f7a93ae497600529ece135823@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock

    * **NOTE:** Type your password and hit enter - even if you can't see it visually!

## Step 3
*   Your testnet blockchain `zbank` is now running successfully. It should show the logs as shown below

## Step 4
*   Add your blockchain nodes of `zbank` to MyCrypto for testing

    * Open the MyCrypto app, then click `Change Network` at the bottom left:

       ![change network](BlockchainPOA/Screenshots/mycrypto_change_network1.png)


    * Select "ZBanknet" as your custom network.

       ![custom network](BlockchainPOA/Screenshots/mycrypto_change_network.png)
    
    * You have now connected MyCrypto to the `ZBanknet` custom network and can acesss its 2 nodes

## Step 5
*   Send money between accounts or nodes

    * Select the `View & Send` option from the left menu pane, then click `Keystore file`.

        ![select_keystore_file](BlockchainPOA/Screenshots/mycrypto_select_keystore.png)

    * On the next screen, click `Select Wallet File`, then navigate to the keystore directory inside your Node1 directory, select the file located there, provide your password for `zbannode1` when prompted and then click `Unlock`.
        ![Unlock_keystore_file](BlockchainPOA/Screenshots/mycrypto_unlock_keystore_zbanknode1.png)
        ![Unlock_key_passwd](BlockchainPOA/Screenshots/mycrypto_unlock_keystore_zbanknode1_passwd.png)

    * This will open your account wallet inside MyCrypto. This is the balance that was pre-funded for this account in the genesis configuration.   

        ![keystore_balance](BlockchainPOA/Screenshots/mycrypto_zbanknode1_balance.png)

    * In the `To Address` box, type the account address from `zbanknode2`, then fill in an arbitrary amount of ETH:

    * Confirm the transaction by clicking "Send Transaction", and the "Send" button in the pop-up window.  

        ![Send transaction](BlockchainPOA/Screenshots/mycrypto_send_txn_zbanknode1_tozbanknode2.png) 
    * Click on `Send`

        ![Confirm_transaction](BlockchainPOA/Screenshots/mycrypto_confirm_txn.png)

    * Click the `Check TX Status` when the green message pops up, confirm the logout:
        ![check_green_status](BlockchainPOA/Screenshots/mycrpto_check_tx_status_popup.png) 

        ![check tx](BlockchainPOA/Screenshots/mycrypto_txn_status_pending.png)

    * You should see the transaction go from `Pending` to `Successful` after the validation is confirmed in the genesis.

    * You can click the `Check TX Status` button to update the status.

    ![successful transaction](BlockchainPOA/Screenshots/mycrypto_txn_status_success.png)

Congratulations, you successfully created your own private blockchain!