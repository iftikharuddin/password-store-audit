<br/>
<p align="center">
<img src="https://res.cloudinary.com/droqoz7lg/image/upload/w_0.5,c_scale/v1697562167/company/mm4xmbdd48iwb7xfsi00.png">
</p>
<br/>

# First Flight #1: PasswordStore Audit by Iftikhar uddin

# PasswordStore

A smart contract application for storing a password. Users should be able to store a password and then retrieve it later. Others should not be able to access the password.

# Audit Report main points:

- The `setPassword` function in the `PasswordStore` contract lacks proper access control modifiers or owner checks, making it vulnerable to unauthorized access
- In `PasswordStore` contract, Replace revert in the '`getPassword`' function with a gas-efficient modifier for access control.
Improvement: Enhance code readability and efficiency by implementing an access control modifier for owner-restricted functions.
- In `PasswordStore` contract `setPassword` Storing plain-text passwords is a severe security risk; secure hashing and salting are essential to protect user data.
- The `DeployPasswordStore.s.sol` script, it's not recommended to pass plain password text/value. Reading it from an environment file (.env) would be a more secure approach

# Thank you

