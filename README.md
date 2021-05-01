# Basic Local Chainlink Node

**Warning:** This is for local development only. Do not use in production.

## What is this?

A self encapsulated environment to run integration tests and develop locally.

It is built using docker-compose using the 0.10.3 chainlink image and the latest postgres image. This does not include a geth container and currently exists to connect to an already running local chain(ganache or hardhat).

## How to use

- Launch local chain (such as `npx hardhat node`)
- Deploy LINK token contract and any other related contracts
- Fund contract with LINK
- Set environment variables in .env such as postgres credentials, LINK_CONTRACT_ADDRESS, and ETH_CHAIN_ID (to match your chain)
- Set username/password in chainlink/.api
- Set keystore password in chainlink/.password
- In docker-compose.yml set your port for ETH_URL (this setup allows for reaching localhost outside of the container aka the host itself. If using linux in your .bashrc in .bash_profile or .zshrc add `export DOCKER_GATEWAY_HOST=172.17.0.1` hattip: https://dev.to/natterstefan/docker-tip-how-to-get-host-s-ip-address-inside-a-docker-container-5anh). If not using local eth node instead use external API from Infura or elsewhere.
- Transfer ETH to Chainlink Node
- In order to test External Adapters/External Bridges appropriately running on your local machine instead of using `http://localhost:8080` for example replace localhost with host.docker.internal such as `http://host.docker.internal:8080` if running geth. It appears that hardhat isn't supported as the rpc doesnt line up to what Chainlink expects.
