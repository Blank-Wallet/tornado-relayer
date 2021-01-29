# Blank's Version of a Tornado Relayer

docker-compose.yml contains a stack that will automatically provision SSL certificates for your domain name and will add a https redirect to port 80.

    Download docker-compose.yml and .env.example

wget https://raw.githubusercontent.com/tornadocash/tornado-relayer/master/docker-compose.yml
wget https://raw.githubusercontent.com/tornadocash/tornado-relayer/master/.env.example -O .env

    Setup environment variables

        set NET_ID (1 for mainnet, 5 for Goerli)

        set HTTP_RPC_URL rpc url for your ethereum node

        set WS_RPC_URL websocket url

        set ORACLE_RPC_URL - rpc url for mainnet node for fetching prices(always have to be on mainnet)

        set PRIVATE_KEY for your relayer address (without 0x prefix)

        set VIRTUAL_HOST and LETSENCRYPT_HOST to your domain and add DNS record pointing to your relayer ip address

        set REGULAR_TORNADO_WITHDRAW_FEE - fee in % that is used for tornado pool withdrawals

        set TORN_ETH_PRICE - TORN/ETH rate that relayer will use to calculate fee for mining claim and swap

        set MINING_SERVICE_FEE - fee in % that is used for mining AP withdrawals

        set REWARD_ACCOUNT - eth address that is used to collect fees

        update AGGREGATOR if needed - Contract address of aggregator instance.

        update CONFIRMATIONS if needed - how many block confirmations to wait before processing an event. Not recommended to set less than 3

        update MAX_GAS_PRICE if needed - maximum value of gwei value for relayer's transaction

        If you want to use more than 1 eth address for relaying transactions, please add as many workers as you want. For example, you can comment out worker2 in docker-compose.yml file, but please use a different PRIVATE_KEY for each worker.

    Run docker-compose up -d

