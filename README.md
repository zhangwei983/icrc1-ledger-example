# ICRC-1 Ledger

This example shows how to run an ICRC-1 ledger locally.

## Download

Currently, I'm using the [9c006a50d364edf1403ef50b24c3be39dba8a5f6](https://github.com/dfinity/ic/releases/tag/release-2024-06-19_23-01-cycle-hotfix) release of IC.

Downloading URLs of the icrc1_ledger:
- wasm: https://download.dfinity.systems/ic/9c006a50d364edf1403ef50b24c3be39dba8a5f6/canisters/ic-icrc1-ledger.wasm.gz
- candid: https://raw.githubusercontent.com/dfinity/ic/9c006a50d364edf1403ef50b24c3be39dba8a5f6/rs/rosetta-api/icrc1/ledger/ledger.did

## Start

Please run the below command to start a local replica.

```bash
dfx start --clean --background
```

## Deploy

Deploy the `icrc1-ledger` canister with below command. Please replace `uovjg-yt3vw-4sz3q-7gqut-7xkv3-yaocz-mcibf-gaxkz-py5ky-pesxv-yqe` with your own principal.

```bash
dfx deploy icrc1-ledger --argument '(variant { Init = record { token_symbol = "TEX"; token_name = "Token example"; minting_account = record { owner = principal "uovjg-yt3vw-4sz3q-7gqut-7xkv3-yaocz-mcibf-gaxkz-py5ky-pesxv-yqe" }; transfer_fee = 10_000; metadata = vec {}; initial_balances = vec {}; archive_options = record { num_blocks_to_archive = 2000; trigger_threshold = 1000; controller_id = principal "uovjg-yt3vw-4sz3q-7gqut-7xkv3-yaocz-mcibf-gaxkz-py5ky-pesxv-yqe"; }; } },)'
```

## Mint

Minting means a transfer call from the minting account to another account.

```bash
dfx canister call icrc1-ledger icrc1_transfer '(record {to = record {owner = principal "5lt2h-5vqvf-tyxrd-uxjcw-6mwm7-ommh5-5vxhi-td72z-fvwls-rqa3o-rqe"}; amount=1_000_000},)'
```

Make sure you call the command with the identity of the minting account.
