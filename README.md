
# docker-electrumx

# requires access to dogecoind (with synced blockchain and rpcuser connectivity to dogecoind)

 read README_INSTALL in /opt/electrumx (and adjust variables)
 cd /
 electrumx_server 
 
> Run an Electrum server with one command

An easily configurable Docker image for running an Electrum server.

## Usage

```
docker run -it -d \
  -v /home/root/electrumx:/data \
  -e DAEMON_URL=http://rpcuser:your_pass_here@127.0.0.1:22555 \
  -e COIN=Dogecoin \
  -p 50101:50101 \
c4pt/electrumx-doge-server

docker exec -it <docker_vm_hash> bash
```

If there's an SSL certificate/key (`electrumx.crt`/`electrumx.key`) in the `/data` volume it'll be used. If not, one will be generated for you.

You can view all ElectrumX environment variables here: https://github.com/spesmilo/electrumx/blob/master/docs/environment.rst

### TCP Port

By default only the SSL port is exposed. You can expose the unencrypted TCP port with `-p 50001:50001`, although this is strongly discouraged.

### WebSocket Port

You can expose the WebSocket port with `-p 50004:50004`.

### RPC Port

To access RPC from your host machine, you'll also need to expose port 8000. You probably only want this available to localhost: `-p 127.0.0.1:8000:8000`.

If you're only accessing RPC from within the container, there's no need to expose the RPC port.

### Version

You can also run a specific version of ElectrumX if you want.

```
docker run -it -d  \
  -v /home/username/electrumx:/data \
  -e DAEMON_URL=http://user:pass@host:port \
  -e COIN=BitcoinSegwit \
  -p 50002:50002 \
c4pt/electrumx-doge-server

docker exec -it <docker_vm_hash> bash
```

