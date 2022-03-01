# Game Mainnet Gentx Submission

- Go version: [v1.17+](https://golang.org/dl/)
- Nibirud version: [v1.0.0](https://github.com/cosmos-gaminghub/nibiru/releases/tag/v1.0.0)


## Schedule
**Submit Gentx**

Until March 9 2022


**Genesis Launch**

March 16th, 2022 11:00 GMT

## genesis params (changed from default)

Check [here](https://github.com/cosmos-gaminghub/mainnet/blob/main/parameter.md) about genesis params for mainnet.


## GenTx Collection

0. Install nibiru
```
git clone https://github.com/cosmos-gaminghub/nibiru.git
cd nibiru && git checkout -b v1.0.0 tags/v1.0.0
make install
```


Make sure to checkout to `v1.0.0` tag.

1. Initialize the nibiru directories and create the local file with the correct chain-id

```
nibirud init <moniker> --chain-id=game-1
```

2. Use the same key you registered in the neuron testnet

```
nibirud keys add <your key name> --recover
```

3. Add the account to your local genesis file with a given amount. Check the amount of GAME in your address [here](https://github.com/cosmos-gaminghub/mainnet/blob/main/accounts/incentivized_testnet_rewards.json).

```
nibirud add-genesis-account $(nibirud keys show <your key name> -a) <your initial bonding amount>ugame
```

4. Create the gentx
Commission rate should NOT be less than 5% for the network decentralization.

You can not bond more than you have.

```
nibirud gentx <your key name> <your initial bond amount>ugame --commission-rate=0.1 --commission-max-rate=1 --commission-max-change-rate=0.1 --pubkey $(nibirud tendermint show-validator) --chain-id=game-1
```

5. Create Pull Request to this repository ([gentxs](./)) with the file `<your validator moniker>.json`.
