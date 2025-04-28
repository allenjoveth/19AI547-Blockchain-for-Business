# Experiment 6: Blockchain-Based Passwordless Authentication (Using Public-Private Key Cryptography)
# Aim:
To implement a secure passwordless authentication system using public-private key cryptography on Ethereum. This prevents phishing and password leaks.

# Algorithm:
Step 1: User Registration
A user registers with their Ethereum public key (instead of a password).


Step 2: Login Process
When logging in, the user signs a random challenge message using their private key.


The smart contract verifies the signature using the user’s public key.



# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract PasswordlessAuth {
    mapping(address => bool) public registeredUsers;

    event UserRegistered(address user);
    event UserAuthenticated(address user);

    function registerUser() public {
        require(!registeredUsers[msg.sender], "Already registered");
        registeredUsers[msg.sender] = true;
        emit UserRegistered(msg.sender);
    }

    function authenticate(bytes32 hash, uint8 v, bytes32 r, bytes32 s) public view returns (bool) {
        require(registeredUsers[msg.sender], "User not registered");
        address signer = ecrecover(hash, v, r, s);
        return signer == msg.sender;
    }
}
```

# Expected Output:
![6 1](https://github.com/user-attachments/assets/4df04fd8-fd92-4091-b17d-12404d2afcda)
![6 2](https://github.com/user-attachments/assets/5b0c2ab6-4f39-4b8f-a15c-0746c6097e98)
![6 3](https://github.com/user-attachments/assets/d521fa92-52f1-47d4-b8fb-d800bced2fa6)
![6 4](https://github.com/user-attachments/assets/49bd5fdd-4c5c-4d74-b3bd-2955a6a8b4a6)

# High-Level Overview:
Eliminates password hacks & phishing attacks.


Uses Ethereum's built-in cryptographic functions.


Inspired by Web3 login solutions like MetaMask authentication.

# RESULT: 
Thus, To implement a secure passwordless authentication system using public-private key cryptography on Ethereum. This prevents phishing and password leaks is executed successfully.
