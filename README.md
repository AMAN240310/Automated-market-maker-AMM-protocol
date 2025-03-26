# SimpleAMM - Aptos AMM Protocol

## Description
SimpleAMM is a minimal Automated Market Maker (AMM) smart contract built in Move for the Aptos blockchain.
It implements a basic liquidity pool with two primary functions: pool creation and token swapping, using the constant product formula (x * y = k).
This project serves as an educational example of AMM mechanics within a concise 40-50 line implementation.

## Vision
SimpleAMM aims to provide developers with a clear, beginner-friendly demonstration of AMM principles on Aptos using Move. 
By keeping the codebase small and focused, it offers an accessible entry point for learning decentralized exchange concepts and Move programming,
with potential for extension into more complex DeFi applications.

## Future Scope
- Implement proper dual-token support with two coin types
- Add liquidity provision and removal functionality
- Introduce fee mechanisms for liquidity providers
- Enhance with robust safety checks and error handling
- Add event emissions for transaction tracking
- Support multiple pool instances per deployment
- Integrate price feed capabilities

## Contract Details for GitHub
- **Module Name**: `MyModule::SimpleAMM`
- **File**: `sources/project.move`
- **Dependencies**:
  - `aptos_framework::signer`
  - `aptos_framework::coin`
  - `aptos_framework::aptos_coin::AptosCoin`
- **Struct**: 
  - `Pool` (capabilities: `key, store`)
    - Fields:
      - `token_x_reserve: u64` (AptosCoin reserve)
      - `token_y_reserve: u64` (Simplified token Y reserve)
      - `k: u64` (Constant product)
- **Functions**:
  1. `create_pool(owner: &signer, initial_x: u64, initial_y: u64)`
     - Initializes pool with initial liquidity
     - Entry function
  2. `swap_x_to_y(trader: &signer, pool_owner: address, x_amount_in: u64)`
     - Swaps token X for token Y
     - Entry function, modifies `Pool` (requires `acquires Pool`)
- **Notes**:
  - Uses AptosCoin as token X, u64 as simplified token Y
  - Token Y output calculated but not transferred (uses assertion)
  - Educational implementation, not production-ready

---
3. Contract Details
    Contract Address: (0x7ba47a4f16186024e4692981eeefb50a4db28c632801d0d2c20692e834ed1183)
   ![image](https://github.com/user-attachments/assets/0799c76c-de4d-4fd7-9c3f-494651f05260)

This project is hosted on GitHub as a reference implementation. Contributions and suggestions for improvement are welcome!
