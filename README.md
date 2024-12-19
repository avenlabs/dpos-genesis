# Genesis Contract Delegate Proof Of Stake

This repo hold all the genesis contracts Based BNB Smart chain. More details in [doc-site](https://docs.bnbchain.org/docs/learn/system-contract).

## Prepare

Install node.js dependency:
```shell script
npm install
curl -sSL https://install.python-poetry.org | python3 -
poetry install
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash
nvm install  12.18.3 && nvm use 12.18.3
```

## Build With JS
```shell
forge install --no-git --no-commit foundry-rs/forge-std@v1.7.3
export RPC_BSC=RPC_LINK
forge test
```

## How to generate genesis file

```bash
1. Edit `init_holders.js` file to alloc the initial BNB holder.
2. Edit `validators.js` file to alloc the initial validator set.
3. Edit system contracts setting as needed.
4. Run `node scripts/generate-genesis.js -c 69696969 -t genesis-template.json -o genesis-mainnnet.json` will generate genesis-mainnnet.json
```

## How to update contract interface for test

```shell script
// get metadata
forge build

// generate interface
cast interface ${workspace}/out/{contract_name}.sol/${contract_name}.json -p ^0.8.0 -n ${contract_name} > ${workspace}/test/utils/interface/I${contract_name}.sol
```

## BEP-171 unlock bot
```shell script
npm install ts-node -g

cp .env.example .env
# set UNLOCK_RECEIVER, OPERATOR_PRIVATE_KEY to .env

ts-node scripts/bep171-unlock-bot.ts 
```

## License

The library is licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0),
also included in our repository in the [LICENSE](LICENSE) file.
