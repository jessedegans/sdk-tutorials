---
order: 8
---

# Client

Now it's time to build the tools for interacting with our app (submitting
transactions, queries, etc). Each module contains a client package that
provides its specific `tx` and `query` client functionality. `tx` for sending transactions containing Messages that update the chain state and `query` for reading the chain state. 

Generally modules provide both a CLI and a REST client  that are bundled together alongside those of the other modules into a single REST server and CLI executable.


Lets start with our CLI. Here we will implement `GetTxCmd` and `GetQueryCmd` for our `greeter`
module's client package. These will then later be used to incorporate
`greeter`'s functionality into our CLI tool.

## TxCmd

For `greeter`'s `TxCmd` we will implement `say`, the command for creating and
sending a greeting to an account address.

Add this to `x/greeter/client/cli/tx.go`

<<< @/hellochain/x/greeter/client/cli/tx.go

## QueryCmd

And for `greeter`'s `QueryCmd` we will implement `list`, the command for
querying our blockchain for all greetings from a given address.

And add this to `x/greeter/client/cli/query.go`

<<< @/hellochain/x/greeter/client/cli/query.go

Ok great now its time to build our CLI tool

## Complete Module

Ok, let's take on more pass at `x/greeter/module.go` to add the functionality
we've implemented.

Update `/x/greeter/module.go` to reflect the following (updated lines
highlighted).

<<< @/hellochain/x/greeter/module.go{12,45,50,50,66}