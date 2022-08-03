# Medic-Chain
A blockchain-based Medical Records Management System

![Screenshot from 2022-04-22 12-12-16](https://user-images.githubusercontent.com/50737863/182576175-b508194b-265b-41a2-897d-9f9d7814b7e4.png)

![Screenshot from 2022-04-22 12-12-40](https://user-images.githubusercontent.com/50737863/182576193-e8db8b92-0b78-4ea7-b180-81b2d0870ff3.png)

![Screenshot from 2022-04-22 12-13-15](https://user-images.githubusercontent.com/50737863/182576236-c21e902a-f7bc-4848-9d46-36099ccaa205.png)

![Screenshot from 2022-04-22 12-14-11](https://user-images.githubusercontent.com/50737863/182576250-ed99cb4d-d9ef-4315-95da-fcdfa07000a3.png)

![Screenshot from 2022-04-22 12-14-42](https://user-images.githubusercontent.com/50737863/182576271-e996fed5-7d16-457e-8237-693b1c344ea9.png)


Today, doctors & health professionals are limited in the level of care they can provide because due to inability to view your complete, accurate health records. The proposed solution is a blockchain network created by the Health Department, who registers the doctors in this network. The doctors can publish patients medical records safely on blockchain network.


## System Requirements

1. Operating System : Ubuntu 16.04
2. System RAM : 4GB or Above

## Step by step instructions for installing / setting up the application for use

**Step 1:** Download the repostory using the command:  
```
 Git Clone "https://github.com/WickedG0d/Medic-Chain.git"
 ```
**Step 2:** Install the dependecies using the command: 
```
 npm Install  
 ```
**Step 3:** Use the following command to compile smart contract:  
```
 truffle compile  
 ```
**Step 4:** Use one of the following commands to connect to the devchain,private or public chain:  

**Devchain:**

1: Run the chain using following command
```
geth --datadir dev --networkid "4002" --http --http.port 8545 --ipcpath "~/.ethereum/geth.ipc" --http.corsdomain "*" --http.api "db,personal,eth,web3,net" --dev
```
2: In new terminal find coin base address and Copy to app.js
```
geth attach
> eth.accounts
```
3: Copy coin base address to app.js.Create 4 more accounts and pass ether to them using following comments
```
personal.newAccount("")//4 times
eth.sendTransaction({from:eth.accounts[0],to:eth.accounts[1],value:100000000000000000000})//pass 100 ether to each account
```
4: Cut the chain and rerun the chain using following comment to unlock the new accounts
```
geth --datadir dev --networkid "4002" --http --http.port 8545 --ipcpath "~/.ethereum/geth.ipc" --http.corsdomain https://remix.ethereum.org --http.api "db,personal,eth,web3,net" --dev --unlock 1,2,3,4 --allow-insecure-unlock
```
*Password: Enter Key*

**Private chain:** 
```
cd geth
```

to create private account
```
geth --identity "miner" --networkid 4002 --datadir data --nodiscover --http --http.port "8545" --port "8191" --ipcpath "~/.ethereum/geth.ipc" --http.corsdomain "*" --http.api "db,eth,net,web3,personal"
```

```
geth --identity "miner" --networkid 4002 --datadir data --nodiscover --mine --http --http.port "8545" --port "8191" --unlock 0,1,2,3 --password password.txt --ipcpath "~/.ethereum/geth.ipc" --http.corsdomain "*" --http.api "db,eth,net,web3,personal" --allow-insecure-unlock 
```

start mining using the following command in new terminal, before doing any transaction:  
```
  geth attach 

  miner.start()  
```
*Password: Enter Key*

**Ropsten:**  

1: Run the chain using following command
```
 geth --testnet --syncmode "light" --datadir "rop" --rpc --rpcapi "db,eth,net,web3,personal" --rpcport "8545"  --rpccorsdomain "*" --allow-insecure-unlock
```
2: use java script console and connect to running chain.
```
    geth attach http://127.0.0.1:8545
```
3: Wait for the node to synch fully (will take some time). use the below command to know the status
```
    eth.syncing
```
    false - incase no synching happening (same for synching finished also), otherwise will show the status

4: Create a new account using the following command
```
    personal.newAccount("")
```
     The password is an enter

    create 3 more accounts

3: Transfer ether to each account using metamask account

4:Cut and ReRun the chain using following command
```
geth --testnet --syncmode "light" --datadir "rop" --rpc --rpcapi "db,eth,net,web3,personal" --rpcport "8545"  --rpccorsdomain "*" -unlock 0,1,2,3 --allow-insecure-unlock
 ```
**Step 5:** Use the following command to deploy the smart contract to the connected chain: 
```
 truffle migrate  
 ```
**Step 6:** Run the dapp using the command  
```
 npm start  
```
## Execution Flow:

**Step 7:** Login as admin to register the doctors. Admin has the privilege to register or delist the doctors.

**Step 8:** Only registered doctors can add health records of patients. The patient registration will be done at this point of time.

**Step 9:** Only registered patients can access the patient login portal. The registered patients can view their health records history. Also the patients can view the health records w.r.t respective doctors.

**Step 10:** Only patients has the privilege to grant access to doctor, so that the doctor can view the respective patients health records for a particular period. The patients can revoke the access given to doctor at any point of time.

**Step 11:** Registered doctors can view patient health records only when access to doctor is given by patient.

END

LinkedIn: https://www.linkedin.com/in/abbas-ali-jamadar-02682b174/
