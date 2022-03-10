# Json-rpc
Users use jsonrpc to interact with `HSC` in the most cases.

# jsonrpc Standards

Hsc supports [json-rpc 2.0](https://www.jsonrpc.org/specification)standard http requests。

request:

```
curl --location --request POST 'https://http-mainnet.hoosmartchain.com' \
--header 'Content-Type: application/json' \
--data-raw '{"jsonrpc":"2.0","id":3,"method":"web3_clientVersion","params":[]}
'
```

success:

```
{"jsonrpc":"2.0","id":67,"result":"Geth/v1.0.0-stable-8ce82ce8/linux-amd64/go1.15.11"}
```

error:

```
{"jsonrpc":"2.0","id":67,"error":{"code":-32601,"message":"the method web3_client does not exist/is not available"}}
```

# json-rpc protocol errors 
<!-- 协议级别的错误 -->

[Specification](http://wiki.geekdream.com/Specification/json-rpc_2.0.html)


| code             | message                    |
| ---------------- | -------------------------- |
| -32700           | Parse error |
| -32600           | Invalid Request    |
| -32601           | Method not found |
| -32602           | Invalid params   |
| -32603           | Internal error   |
| -32000 to -32099 | Server error     |

# Hsc json-rpc errors

[eip-1474](https://eips.ethereum.org/EIPS/eip-1474#error-codes)；


| Code   | Message                        | Category     |
| ------ | ------------------------------ | ------------ |
| -32000 | Invalid input     | non-standard |
| -32001 | Resource not found         | non-standard |
| -32002 | Resource unavailable       | non-standard |
| -32003 | Transaction rejected       | non-standard |
| -32004 | Method not supported       | non-standard |
| -32005 | Limit exceeded             | non-standard |
| -32006 | JSON-RPC version not supported | non-standard |


# web3 sdk json-rpc errors

[eip-1193](https://eips.ethereum.org/EIPS/eip-1193#provider-errors)

| Status code | Name                  |
| ----------- | --------------------- |
| 4001        | User Rejected Request  | 
| 4100        | Unauthorized         |
| 4200        | Unsupported Method   |
| 4900        | Disconnected |
| 4901        | Chain Disconnected |