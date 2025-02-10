
# Move Vault

## Overview

Move Vault is a smart contract module for the Aptos blockchain that enables users to deposit and withdraw coins securely. It supports multiple coin types and ensures that deposits and withdrawals can be paused and resumed by an admin.

## Features

-   **Vault Management**: Admins can initialize a vault and add different coin types.
    
-   **Deposits and Withdrawals**: Users can deposit supported coins and withdraw them when needed.
    
-   **User Management**: Ensures that users exist in the system before allowing transactions.
    
-   **Pause & Unpause Operations**: Admins can pause and unpause deposits and withdrawals.
    
-   **Security**: Ensures that only authorized admins can manage the vault.
    
-   **Testing**: Includes unit tests to validate core functionalities.
    

## Installation

1.  Ensure you have the Aptos CLI installed.
    
2.  Clone the repository:
    
    ```
    git clone https://github.com/luan957/move-vault.git
    cd move-vault
    ```
    
3.  Compile the Move module:
    
    ```
    aptos move compile
    ```
    
4.  Run the tests:
    
    ```
    aptos move test
    ```
    

## Usage

### Initializing the Vault

```
public entry fun init_vault(admin: &signer)
```

-   Must be called by the admin to set up the vault.
    

### Adding a New Coin

```
public entry fun admin_add_coin<CoinType>(admin: &signer)
```

-   Admin can add a new coin type to the vault.
    

### Depositing Coins

```
public entry fun deposit<CoinType>(sender: &signer, amount: u64)
```

-   Users can deposit coins into the vault.
    

### Withdrawing Coins

```
public entry fun withdraw<CoinType>(sender: &signer, amount: u64)
```

-   Users can withdraw coins from the vault.
    

### Pause Vault Operations

```
public entry fun pause(admin: &signer)
```

-   Admin can pause deposits and withdrawals.
    

### Unpause Vault Operations

```
public entry fun unpause(admin: &signer)
```

-   Admin can resume deposits and withdrawals.
    

## Error Codes

-   **ENOT_ADMIN (0)**: Only the admin can perform this action.
    
-   **ECOIN_NOT_EXISTS (1)**: The requested coin type does not exist in the vault.
    
-   **EDEPOSIT_WITHDRAWL_PAUSED (2)**: Deposits and withdrawals are currently paused.
    

## Testing

The module includes various test cases to verify functionality:

-   **test_deposit_success**: Ensures successful deposits.
    
-   **test_deposit_fail**: Tests failure scenarios for deposits.
    
-   **test_withdraw_success**: Ensures successful withdrawals.
    
-   **test_withdraw_fail**: Tests failure scenarios for withdrawals.
    
-   **test_pause**: Ensures deposits are blocked when paused.
    
-   **test_unpause**: Ensures deposits resume after unpausing.
    

To run the tests, execute:

```
aptos move test
```

## License

This project is licensed under the MIT License.
