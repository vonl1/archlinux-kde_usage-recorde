### 问题

```shell
docker run -d -p8080:80 xxxx/xxxx

docker: Error response from daemon: 
failed to create endpoint vibrant_lamport on network bridge: 
failed to add the host (veth6ae98d1) <=> sandbox (veth4018dcf) pair interfaces: operation not supported.
```

### 产生原因

archlinux 更新了内核,然后你电脑没重启更新就会出现这个问题

### 解决办法:重启电脑

>https://github.com/moby/moby/issues/27426
