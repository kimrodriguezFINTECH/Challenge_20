### Background

A fintech startup company has recently hired you. This company is disrupting the finance industry with its own cross-border, Ethereum-compatible blockchain that connects financial institutions. Currently, the team is building smart contracts to automate many of the institutions’ financial processes and features, such as hosting joint savings accounts.

To automate the creation of joint savings accounts, you’ll create a Solidity smart contract that accepts two user addresses. These addresses will be able to control a joint savings account. Your smart contract will use ether management functions to implement a financial institution’s requirements for providing the features of the joint savings account. These features will consist of the ability to deposit and withdraw funds from the account.

### What You're Creating

* The completed Solidity `JointSavings` smart contract.

* A folder named `Execution_Results` that contains at least eight images. These images should confirm that the deposit and withdrawal transactions, which are designed to test the `JointSavings` functionality in the JavaScript VM, worked as expected.

### Instructions

The steps for this homework are divided into the following sections:

1. Create a Joint Savings Account Contract in Solidity

2. Compile and Deploy Your Contract in the JavaScript VM

3. Interact with Your Deployed Smart Contract

#### Step 1: Create a Joint Savings Account Contract in Solidity

1. From the provided [starter code](Starter_Code), open the Solidity file named `joint_savings.sol` in the Remix IDE.

2. Define a new contract named `JointSavings`.

3. Define the following variables in the new contract:

    * Two variables of type `address payable` named `accountOne` and `accountTwo`

    * A variable of type `address public` named `lastToWithdraw`

    * Two variables of type `uint public` named `lastWithdrawAmount` and `contractBalance`

<img width="918" alt="Screenshot 2024-05-05 at 4 53 25 PM" src="https://github.com/kimrodriguezFINTECH/Challenge_20/assets/152752672/5b85c00e-0e62-4926-93ce-96d39668e715">


4. Define a function named `withdraw` that accepts two arguments: `amount` of type `uint` and `recipient` of type `payable address`. In this function, code the following:

    * Define a `require` statement that checks if `recipient` is equal to either `accountOne` or `accountTwo`. If it isn’t, the `require` statement returns the “You don't own this account!” text.

    * Define a `require` statement that checks if `balance` is sufficient for accomplishing the withdrawal operation. If there are insufficient funds, it returns the “Insufficient funds!” text.

    * Add an `if` statement to check if `lastToWithdraw` is not equal (`!=`) to `recipient`. If it’s not equal, set it to the current value of `recipient`.

    * Call the `transfer` function of the `recipient`, and pass it the `amount` to transfer as an argument.

    * Set `lastWithdrawAmount` equal to `amount`.

    * Set the `contractBalance` variable equal to the balance of the contract by using `address(this).balance` to reflect the new balance of the contract.

<img width="937" alt="Screenshot 2024-05-05 at 5 00 41 PM" src="https://github.com/kimrodriguezFINTECH/Challenge_20/assets/152752672/1eddd166-4254-45fc-b3e3-e2b6229cd9e5">

5. Define a `public payable` function named `deposit`. In this function, code the following:

    * Set the `contractBalance` variable equal to the balance of the contract by using `address(this).balance`.

6. Define a `public` function named `setAccounts` that takes two `address payable` arguments, named `account1` and `account2`. In the body of the function, set the values of `accountOne` and `accountTwo` to `account1` and `account2`, respectively.

7. Add a fallback function so that your contract can store ether that’s sent from outside the deposit function.

<img width="937" alt="Screenshot 2024-05-05 at 5 02 03 PM" src="https://github.com/kimrodriguezFINTECH/Challenge_20/assets/152752672/627f6f4e-9e73-4af5-a030-3c1045b09aa9">


#### Step 2: Compile and Deploy Your Contract in the JavaScript VM

1. Compile your smart contract. If an error occurs, review your code, and make the necessary changes for a successful compilation.

2. In the Remix IDE, navigate to the “Deploy & Run Transactions” pane, and then make sure that “JavaScript VM” is selected as the environment.

3. Click the Deploy button to deploy your smart contract, and then confirm that it successfully deployed.

<img width="1288" alt="Screenshot 2024-05-05 at 4 45 43 PM" src="https://github.com/kimrodriguezFINTECH/Challenge_20/assets/152752672/241bffa2-0443-44c8-ab90-e9d00965be4b">

#### Step 3: Interact with Your Deployed Smart Contract

Now that your contract is deployed, it’s time to test its functionality! After each step, capture a screenshot of the execution, and then save it in a folder named `Execution_Results`. You’ll share this folder with your final submission.

To interact with your deployed smart contract, complete the following steps:

1. Use the `setAccounts` function to define the authorized Ethereum address that will be able to withdraw funds from your contract.

     > **Note** You can either use the following Ethereum addresses or create new, dummy addresses on the [Vanity-ETH](https://vanity-eth.tk/) website, which includes an Ethereum vanity address generator.
    >
    > ```text
    > Dummy account1 address: 0x0c0669Cd5e60a6F4b8ce437E4a4A007093D368Cb
    > Dummy account2 address: 0x7A1f3dFAa0a4a19844B606CD6e91d693083B12c0
    > ```

2. Test the deposit functionality of your smart contract by sending the following amounts of ether. After each transaction, use the `contractBalance` function to verify that the funds were added to your contract:

    * Transaction 1: Send 1 ether as wei.

<img width="1414" alt="Screenshot 2024-05-04 at 3 28 47 PM" src="https://github.com/kimrodriguezFINTECH/Challenge_20/assets/152752672/2ae8d4cd-51ab-46f8-b2e7-b6c55487748f">

    * Transaction 2: Send 10 ether as wei.
    
<img width="1418" alt="Screenshot 2024-05-04 at 3 29 43 PM" src="https://github.com/kimrodriguezFINTECH/Challenge_20/assets/152752672/1b7c7919-b782-4bd2-9f70-6930051d1ed9">

    * Transaction 3: Send 5 ether.

<img width="1412" alt="Screenshot 2024-05-04 at 3 30 09 PM" src="https://github.com/kimrodriguezFINTECH/Challenge_20/assets/152752672/df32fe84-8d4a-4ae2-9ef4-1bfae02cc5c1">


    > **Note** Remembering how to convert ether to wei and vice versa can be challenging. So, you can use a website like [Ethereum Unit Converter](https://eth-converter.com/) to ease doing the conversion.

3. Once you’ve successfully deposited funds into your contract, test the contract’s withdrawal functionality by withdrawing 5 ether into `accountOne` and 10 ether into `accountTwo`. After each transaction, use the `contractBalance` function to verify that the funds were withdrawn from your contract. Also, use the `lastToWithdraw` and `lastWithdrawAmount` functions to verify that the address and amount were correct.
   
* Transaction 1: Withdrawing 5 ether into `accountOne`
  
<img width="1412" alt="Screenshot 2024-05-04 at 3 40 36 PM" src="https://github.com/kimrodriguezFINTECH/Challenge_20/assets/152752672/bf5b43c6-d4b9-4890-97ea-48389dbe0885">

* Transaction 2: Withdrawing 10 ether into `accountTwo`

<img width="1416" alt="Screenshot 2024-05-04 at 3 42 04 PM" src="https://github.com/kimrodriguezFINTECH/Challenge_20/assets/152752672/849cf81b-d643-4bc4-8fc3-bee3c24bb6ff">


---
