### NFS pv demo

使用 NFS 作为 Persistent Volume 的 Backend。

首先，请确保有一台 NFS Server，比如说： 10.0.9.30，并 export 了 /data/k8s 目录。
然后修改 `nfs-pv.yaml` 中的 nfs 配置为你的 nfs server 地址和路径。

```
kubectl apply -f nfs-pv.yaml
kubectl apply -f nfs-pvc.yaml
kubectl apply -f nfs-busybox-rc.yaml
kubectl apply -f nfs-busybox-rc2.yaml
```
 nfs-busybox-rc 和 nfs-busybox-rc2　共用同一个 pvc，通过 volume 的 subPath 来区分各自的目录。
