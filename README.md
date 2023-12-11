## 💻 Node Management Scripts & Best Practices

- [htlcScan.sh](/htlcScan.sh): scans through incoming and outgoing htlcs calculating expiration heights. Sends messages over Telegram in case of high number of pending htlcs (>10, configurable). If htlcs are about to expire (< 13 blocks), the script disconnects both parties up and downstream the route and thus tries to resolve pending htlcs.
- [check-torpeers.sh](/check-torpeers.sh): scans through connected peers and tries to switch hybrid peers currently connected to Tor to their respective clearnet address(es).
- [bosLogRawTx.service](/bosLogRawTx.service): a simple background service logging every onchain transaction and its transaction hex made by the node to republish the hex at a later time, if necessary.
- [bosRules.service](/bosRules.service): a simple background service that enforces a rich set of rules to incoming channel requests. See description in service file for some examples what it is capable of.
- [private-trusted-zero-conf-channels](/private-trusted-zero-conf-channels.md): short overview on how to setup private-trusted zero-conf channels between a routing node (LND) and Blixt Wallet app (neutrino-backed LND mobile node w/ enabled zero-conf channel acceptor).
- [anchor_check.sh](/anchor_check.sh): this script shows all of your channel peers' anchors commit fee-rates in ascending order. Indicating high risk, once you identify a small commitment fee in high-mempool fee environment. Your force-close fee won't be enough and you'll run into a CPFP for your commitment tx to get into the next 2 blocks. Mitigation might be to lower traffic with high fees and minimize rebalancing.
- [checkChannelUpdates.sh](/checkChannelUpdates.sh): outputs the top 10 channels with the most updates. Additionally, it provides the total sum of all state updates of the node.
- [healthmonitor.sh](/healthmonitor.sh): monitors system resource usage and sends warnings to Telegram if specific thresholds are exceeded. It checks the usage of memory, swap memory, disk storage and long-term CPU usage (15-minutes average). The user is notified via Telegram bot when any of these resources surpass predefined thresholds. The script also uses `bitcoin-cli` to compare the local blockheight with the majority of connected peers and reports any deviation.
___________________________________
🏆 Credits to feelancer21, M1CH43LV, RocketNodeLN, ziggie1984, TrezorHannes, weasel3 et al.
