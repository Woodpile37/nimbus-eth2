# Sync your node

Before you can use your node, it needs to sync with the network.
Syncing starts automatically when you start your node, and may take **several hours**, or even days, depending on the performance of your hardware.

!!! tip
    To get started more quickly, you can perform a [trusted node sync](./trusted-node-sync.md) instead.
    This requires access to a synced node or a third-party service.


If you are planning to become a validator, you should ensure that your beacon node is [completely synced](./keep-an-eye.md#keep-track-of-your-syncing-progress) before submitting your deposit; otherwise, you might miss attestations, proposal duties and sync committee duties until it has finished syncing.

!!! note
    You need need to run an execution client (**web3 provider**) together with the beacon node.
    See [here](./eth1.md) for instructions on how to do so.

## Networks

Using Nimbus, you can connect either to a testnet or mainnet.
Mainnet is the main Ethereum network where real assets are at stake, while testnets are used by users and developers alike to test their node and setup before committing real assets.

If this is the first time you're setting up your node, it is recommended you run it on a testnet first.
Later, when everything is working, you can easily switch to mainnet.

=== "Testnet"

    To start syncing the `holesky` testnet from the `nimbus-eth2` repository, run:

    ```
     ./run-holesky-beacon-node.sh
    ```

=== "Mainnet"

    To start syncing the Ethereum beacon chain mainnet, run:

    ```
     ./run-mainnet-beacon-node.sh
    ```

## Log output

You should see the following output:

```
INF 2023-10-01 11:25:33.487+01:00 Launching beacon node
...
INF 2023-10-01 11:25:34.556+01:00 Loading block dag from database            topics="beacnde" tid=19985314 path=build/data/shared_holesky_0/db
INF 2023-10-01 11:25:35.921+01:00 Block dag initialized
INF 2023-10-01 11:25:37.073+01:00 Generating new networking key
...
NOT 2023-10-01 11:25:59.512+00:00 Eth1 sync progress                         topics="eth1" tid=21914 blockNumber=3836397 depositsProcessed=106147
NOT 2023-10-01 11:26:02.574+00:00 Eth1 sync progress                         topics="eth1" tid=21914 blockNumber=3841412 depositsProcessed=106391
...
INF 2023-10-01 11:26:31.000+00:00 Slot start                                 topics="beacnde" tid=21815 file=nimbus_beacon_node.nim:505 lastSlot=96566 scheduledSlot=96567 beaconTime=1w6d9h53m24s944us774ns peers=7 head=b54486c4:96563 headEpoch=3017 finalized=2f5d12e4:96479 finalizedEpoch=3014
INF 2023-10-01 11:26:36.285+00:00 Slot end                                   topics="beacnde" tid=21815 file=nimbus_beacon_node.nim:593 slot=96567 nextSlot=96568 head=b54486c4:96563 headEpoch=3017 finalizedHead=2f5d12e4:96479 finalizedEpoch=3014
...
```

## Data directory

While running, the beacon node will store chain data and other information its data directory, which by default is found in `build/data`.
For more information, see the [data directory guide](./data-dir.md).

## Command line options

You can add command line options to the startup command.
For example, to change the port to 9100, use:

```sh
./run-holesky-beacon-node.sh --tcp-port=9100 --udp-port=9100
```

To see a list of the command line options available to you, with descriptions, run:

```
./build/nimbus_beacon_node --help
```

More information is available from the [options](./options.md) page.

## Keep track of your sync progress

See [here](./keep-an-eye.md#keep-track-of-your-syncing-progress) for how to keep track of your sync progress.
