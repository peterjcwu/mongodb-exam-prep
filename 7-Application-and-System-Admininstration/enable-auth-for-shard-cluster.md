# Enable Auth for Shard Cluster

For a shared cluster, the user infroamtions are stored in the **configuration servers**.

If you would like to disable the localhost excption, you need to<code>  --setParameter enableLocalHostAuthBypass=false</code> in the mongod option.

There is no --auth option for mongos


## Config file

```yaml
security:
    authorization: 'enabled'
```