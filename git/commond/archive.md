查看帮助
```shell script
 git archive [options] <tree-ish> [<path>...]
 -o, --output <file>   write the archive to this file
 -0                    store only
 -1                    compress faster
 -9                    compress better
 -l, --list            list supported archive formats
```
运行`git archive --list`查看支持的归档格式有`tar、tgz、tar.gz、zip`
```shell script
#导出最新的版本库
git archive -o ../latest.zip HEAD
#导出指定提交记录
git archive -o ../git-1.4.0.tar 8996b47 
#导出一个目录
git archive -o ../git-1.4.0-docs.zip  HEAD:Documentation/  
#导出为tar.gz格式
git archive   8996b47 | gzip > ../git-1.4.0.tar.gz
```

导出最后一次提交修改过的文件
```shell script
git archive -o ../updated.zip HEAD $(git diff --name-only HEAD^)
```