- A private IP is an IP address reachable only between servers in the same network; however, it is unreachable over the internet.
- Consider using cache when data is read frequently but modified infrequently.
- Caching infrequently used assets provides no significant benefits so
you should consider moving them out of the CDN.
-  **geoDNS** is a DNS service that allows domain
names to be resolved to IP addresses based on the location of a user.
- Sharding separates large databases into smaller, more easily managed parts called shards.
Each shard shares the same schema, though the actual data on each shard is unique to the
shard.
- Summary of how we scale our system to support millions of users:
    - Keep web tier stateless
    - Build redundancy at every tier
    - Cache data as much as you can
    - Support multiple data centers
    - Host static assets in CDN
    - Scale your data tier by sharding
    - Split tiers into individual services
    - Monitor your system and use automation tool
- List of popular rate limiting algorithms:
   - Token bucket
   - Leaking bucket
   - Fixed window counter
   - Sliding window log
   - Sliding window counter
- **Consistent hashing** is a commonly used technique to distribute requests/data evenly and efficiently across servers.

## Things to learn
- Multi-master replication
- Circular replication
- Paxos
- Raft
- Caching strategies (eg. Read-through-cache)
- Scaling memecached at facebook (paper)
- Cache eviction strategies
- Dynamic content caching
- GeoDNS
- BGP
- rate limiting algorithms