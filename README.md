## Build etcd docker image

    ./build.sh

or get the image with following command (don't run yet)

    docker pull unmerged/etcd

## Deploy an etcd cluster

1. Deploy the first etcd peer

  ```
  ./deploy-first-node.sh <ip of the host>
  ```
  
  The host is the machine you want to deploy the first peer to. 
  
  *Note* the ip must be accessable by other peers.

  At the end of a successful running, the first peer's client url will be shown. Write it down - you will need it in the second step.

2. Deploy following peers

  ```
  ./deploy-following-node.sh <a peer's client url> <ip of THIS peer's host>
  ```
  
  A peer's client url has the format *ip:port*. Upon a successful running, this peer's client url will be shown at the end. You can repeat step 2 to deploy as many peers as possible in the cluster.

3. Test the cluster

  ```
  etcdctl --endpoint=<client urls> member list
  ```
  
That's it!
