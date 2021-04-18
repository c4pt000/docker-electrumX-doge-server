![s1](https://raw.githubusercontent.com/c4pt000/electrum-wallet-for-dogecoin/master/donate-about-deposit.png)

# docker-electrumx

for docker-dogecoind-full 50GB 
 
 * 04-16-2021 sync
 
 docker run -it -d -p 22555:22555 -p 22556:22556 c4pt/dogecoind-current-full
 
 docker exec -it <docker_vm_hash> bash
 

dogecoin.conf: /root/.dogecoin/dogecoin.conf -> c4pt/dogecoind-current-FULL
```
rpcpassword=yourpasswordhere
rpcuser=rpcuser
mempoolexpiry=24
dbcache=1000
server=1
port=22556
rpcport=22555
rpcallowip=127.0.0.1


addnode=95.85.29.144
addnode=162.243.113.110
addnode=146.185.181.114
addnode=188.165.19.28
addnode=166.78.155.36
addnode=doge.netcodepool.org
addnode=doge.cryptoculture.net
addnode=dogepool.pw
addnode=78.46.57.132


addnode=core0-gb.dogecoin.gg
addnode=core1-gb.dogecoin.gg
addnode=dnf-1.gbf.re
addnode=dnf-1.gbf.re
addnode=dnf-2.gbf.re
addnode=dnf-2.gbf.re
addnode=dnf-3.gbf.re
addnode=dnf-3.gbf.re
addnode=dnf-4.gbf.re
addnode=dnf-4.gbf.re
addnode=dnf-alpha.gbf.re
addnode=dnf-beta.gbf.re
addnode=dnf-test.gbf.re
addnode=doge1-eu.langerhans.de
addnode=doge1-eu.langerhans.de
addnode=doge2-eu.langerhans.de
addnode=doge2-eu.langerhans.de
addnode=doge3-eu.langerhans.de
addnode=doge3-eu.langerhans.de
addnode=doge4-eu.langerhans.de
addnode=doge4-eu.langerhans.de
addnode=dogenode.11z.me:22556
addnode=eu1.5trubel.de
addnode=eu2.5trubel.de
addnode=superfastdoge.ddns.net
addnode=us-1.wowsuchfast.com
addnode=us-2.wowsuchfast.com
```

# requires access to dogecoind (with synced blockchain and rpcuser connectivity to dogecoind)

see -> https://github.com/c4pt000/Docker-dogecoin-images

* for dogecoind compressed synced images

 read README_INSTALL in /opt/electrumx (and adjust variables)
 cd /
 electrumx_server 
 
> Run an Electrum server with one command

An easily configurable Docker image for running an Electrum server.

## Usage
also set --> /etc/electrum-doge.conf
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

