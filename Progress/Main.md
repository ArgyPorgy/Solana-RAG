# Soc-rag?

## Points covered 
### API ??
- https://streaming.bitquery.io/eap
using this api as of now 
```
import json

url = "https://streaming.bitquery.io/graphql"

payload = json.dumps({
   "query": "query MyQuery {\n  EVM {\n    Transactions\n    Transfers\n    BalanceUpdates\n  }\n}\n",
   "variables": "{}"
})
headers = {
   'Content-Type': 'application/json',
   'X-API-KEY': 'BQYGb0sj7lQvqR8xiktkc1mVWOcmYjyn',
   'Authorization': 'Bearer ory_at_P68byxEGrv9e-pqKl8yN3DPzZB4-G1gUMOuYDk5ArnE.uP7zb4suE7pquhNdcNA2eNV9lN9SF65sKt--OPyJQ1E'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```
to model for someting like 
```
        subscription($tx:String!) {
  Solana {
    InstructionBalanceUpdates(
      limit: {count: 10}
      where: {BalanceUpdate: {Currency: {Fungible: false}, Account: {Address: {includes: $tx}}}}
    ) {
      Transaction {
        Index
        FeePayer
        Fee
        Signature
        Result {
          Success
          ErrorMessage
        }
      }
      Instruction {
        InternalSeqNumber
        Index
        CallPath
        Program {
          Address
          Name
          Parsed
        }
      }
      Block {
        Time
        Hash
        Height
      }
      BalanceUpdate {
        Account {
          Address
          Token {
            Owner
          }
        }
        Amount
        Currency {
          Decimals
          CollectionAddress
          Name
          Key
          IsMutable
          Symbol
        }
      }
    }
  }
}
```


- find out how to actually get the subcription working 
- time how much should it last ?
- openning a subcription gives multiple things 
        paginate them or how to make it work ??

### LLM
- todo
- how to take response and feed it 
- write the actuall queries ?
- other stuff

remaining stuffff