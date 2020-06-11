### mac环境下

- 查看ssh key
```shell script
-ls -al ~/.ssh
```
- 生成ssh key
```shell script
  .ssh ssh-keygen -t rsa -C "xujw@irongbei.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/xujw/.ssh/id_rsa): id_rsa.gitlab
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in id_rsa.gitlab.
Your public key has been saved in id_rsa.gitlab.pub.
The key fingerprint is:
SHA256:Mm9ZkEVI1X6CMA4NGBbUyUGG2niP1MdQ9CRyPQjcIN8 xujw@irongbei.com
The key's randomart image is:
+---[RSA 3072]----+
|   .*XO%**=.     |
|   .o+B+B*o .    |
|   + ..=Eo.+     |
|  o + . +.. o .  |
|   o oo.S .  o   |
|    . .+ o       |
|        +        |
|       .         |
|                 |
+----[SHA256]-----+
```
- 将新生成的key添加到ssh-agent中
```shell script
ssh-add ~/.ssh/id_rsa
```

### windows环境
```shell script
  .ssh ssh-keygen -t rsa -C "xujw@irongbei.com"
```