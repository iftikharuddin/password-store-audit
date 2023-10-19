# First Flight #1: PasswordStore Audit by Iftikhar Uddin for CodeHawk

# Summary

This audit report covers the security analysis of the `PasswordStore` smart contract. The contract is designed for securely storing and retrieving passwords, and a deployment script `(DeployPasswordStore.s.sol)` has been included.

# Vulnerability Details

1 - **Access Control Lacking in setPassword Function:**
    
- The `setPassword` function in the `PasswordStore` contract lacks proper access control modifiers or owner checks, making it vulnerable to unauthorized access.

2 - **Revert Usage in getPassword Function:**

- In the `PasswordStore` contract, replace the use of `revert` in the `getPassword` function with a gas-efficient modifier for access control.
- Improvement: Enhance code readability and efficiency by implementing an access control modifier for owner-restricted functions.

3 - **Storage of Plain-Text Passwords:**

- In the `PasswordStore` contract, the `setPassword` function stores plain-text passwords, which is a severe security risk.
- Secure hashing and salting should be implemented to protect user data.

4 - **Password Handling in Deployment Script:**

- In the `DeployPasswordStore.s.sol` script, it is not recommended to pass plain password text/values directly.
- A more secure approach would be to read passwords from an environment file (e.g., .env).

# Impact

- Lack of access control in `setPassword` function can lead to unauthorized changes to the stored password.
- The use of `revert` for access control in the `getPassword` function results in higher gas costs for unauthorized users.
- Storing plain-text passwords poses a significant security risk, making user data vulnerable.
- Passing plain passwords in the deployment script can lead to potential exposure of sensitive information.

# Tools used:

- The audit was conducted using manual code review and best practices in smart contract security.

# Recommendations

1 - Implement access control modifiers or owner checks in the `setPassword` function to restrict unauthorized access.

2 - Replace the use of `revert` with a gas-efficient modifier in the `getPassword` function for enhanced security and efficiency.

3 - Secure user data by implementing a password hashing and salting mechanism in the `setPassword` function.

4 - In the deployment script (`DeployPasswordStore.s.sol`), consider reading sensitive data like passwords from an environment file (e.g., .env) rather than passing them directly in the script.

    
# Thank you

