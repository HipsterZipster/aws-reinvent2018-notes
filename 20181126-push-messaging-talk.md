## Speaker

Susheel Aroskar
senior software engineer
saroskar@netflix.com

PUSH = Persist Until Something Happens

# Zuul Push Architecture

- Handles 40 million concurrent connections at peak

- C10k challenges - handles 10k concurrent connections on a single box

## Thread per connection model

- thread1 -> socket1 -> read/write

## Async i/o model

- single thread
- read callback
- write callback

## Netty ChannelHandler Pipeline

- async node-js like approach
- cant use local state, must have a form of finite state machine
- plug in your own custom authenticatiop policy

## Push Registry Features Checklist

- low read latency (writes once when client registers, but is read for every message)
- automatic record expiry
- sharding
- replication

## They use Dynomite for our push regitry

redis

- auto-sharding
- read/write quorum
- cross-region compaitiblity

Kafka message queues

- Fire and forget message delivery

- use different queues for different priorities

- persistent connectoins make zuul push server stateful
- long-lived stable connections are great for client efficiency, but they are terrible for quick deploy or roll-back

- if you love your clients, set them free by tearing down connections periodically

- randomize each connection's lifetime to automatically dampen any reconnect storms

- use big server to handle tons of connections
  ulimit -n 262144
  net.ipv5.tcp_rmem

- how to auto-scale push cluster?

* classic load balancers do not proxu websockets

# Recap of push operation best practices

- recycle connectoins periodcically
- renadomize connection lifetime
- more small servers >> few BIG servers
- auto-scale on number of open connection per box and not number of cpus
- either use ALB or CLB in TCP mode for load balancing

- github.com/Netflix/zuul
