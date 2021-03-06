# Helloworld in grpc-elixir

This example is originally found in [this repo](https://github.com/tony612/grpc-elixir).
Since this example is being run in the [BoxBox](https://github.com/renderedtext/boxbox) environment,
client (`prvi/client.exs`) is connecting to `boxbox:50051`.
In general, it can be replaced, e.g with `localhost:50051`.

## Usage

1. Install deps and compile
```shell
$ mix do deps.get, compile
```

2. Run the server
```shell
$ mix grpc.server
```

3. Run the client script
```shell
$ mix run priv/client.exs
```

## Regenerate Elixir code from proto

1. Modify the proto `priv/protos/helloworld.proto`
2. Install `protoc` [here](https://developers.google.com/protocol-buffers/docs/downloads)
3. Install `protoc-gen-elixir`
```
mix escript.install hex protobuf
```
4. Generate the code:
```shell
$ protoc -I priv/protos --elixir_out=plugins=grpc:./lib/ priv/protos/helloworld.proto
```

Refer to [protobuf-elixir](https://github.com/tony612/protobuf-elixir#usage) for more information.

## How to start server when starting your application?

Change the config to:

```elixir
config :grpc, start_server: true
```
