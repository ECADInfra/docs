
# Public Tezos RPC Nodes by ECADInfra

We provide free access to public Tezos RPC nodes for both **Mainnet** and **Ghostnet** networks. These nodes are designed to support the Tezos ecosystem, ensuring that developers and users can easily access necessary RPC endpoints.

## Available RPC Endpoints
Our nodes can be accessed at the following endpoints:
- **Mainnet:** `https://mainnet.ecadinfra.com/`
- **Ghostnet:** `https://Ghostnet.ecadinfra.com/`

Our nodes allow access to the following RPC paths. If you require additional RPC paths, feel free to contact us at [ops@ecadlabs.com](mailto:ops@ecadlabs.com), and we will do our best to accommodate your needs.

### Allowed Mainnet & Ghostnet RPC Paths

#### General Chain Data:
- `/chains/<chain_id>/blocks`
- `/chains/<chain_id>/blocks/<block_id>`
- `/chains/<chain_id>/chain_id`
- `/chains/<chain_id>/checkpoint`

#### Block Context Information:
- `/chains/<chain_id>/blocks/<block_id>/context/constants`
- `/chains/<chain_id>/blocks/<block_id>/context/contracts/<contract_id>`
- `/chains/<chain_id>/blocks/<block_id>/context/delegates/<delegate_id>`
- `/chains/<chain_id>/blocks/<block_id>/context/total_supply`
- `/chains/<chain_id>/blocks/<block_id>/context/issuance`
- `/chains/<chain_id>/blocks/<block_id>/context/nonces/<nonce_id>`
- `/chains/<chain_id>/blocks/<block_id>/context/liquidity_baking/<lb_id>`

#### Block Metadata:
- `/chains/<chain_id>/blocks/<block_id>/metadata`
- `/chains/<chain_id>/blocks/<block_id>/operation_hashes`
- `/chains/<chain_id>/blocks/<block_id>/operations`

#### Block Header Information:
- `/chains/<chain_id>/blocks/<block_id>/header`
- `/chains/<chain_id>/blocks/<block_id>/header/<header_hash>`

#### Operations:
- `/chains/<chain_id>/blocks/<block_id>/helpers/forge/operations`
- `/chains/<chain_id>/blocks/<block_id>/helpers/scripts/run_operation`
- `/chains/<chain_id>/blocks/<block_id>/helpers/scripts/pack_data`

#### Network and Version Information:
- `/network/stat`

#### Mempool Information:
- `/chains/<chain_id>/mempool/filter`
- `/chains/<chain_id>/mempool/pending_operations`

#### Monitoring:
- `/monitor/active_chains`
- `/monitor/heads/main`

## Important Notes

1. **Rolling Nodes:**  
   Our public nodes are rolling nodes, which means they retain a limited amount of blockchain history. Rolling nodes keep the current block data and a set number of previous blocks, but they do not retain the entire chain history. For historical queries beyond this limit, alternative nodes may be required.

2. **Cloudflare Security:**  
   We use **Cloudflare** for load balancing and security. Sometimes Cloudflare may block certain IP addresses. If you encounter difficulties accessing the RPC nodes, please try accessing them from a different IP address.

3. **404 Not Found Errors:**  
   If an RPC you attempt to access returns a **404 Not Found** error, this could mean that the RPC path is not enabled on our public nodes. However, if this endpoint works on other nodes, please reach out to us at [ops@ecadlabs.com](mailto:ops@ecadlabs.com), and we’ll work to enable access where reasonable.

