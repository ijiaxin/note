### linux复制指定目录下的全部文件到另一个目录
假设复制源目录 为 `dir1` ,目标目录为`dir2`。怎样才能将`dir1`下所有文件复制到`dir2`下了
如果`dir2`目录不存在，则可以直接使用
`cp -r dir1 dir2`
即可。
如果`dir2`目录已存在，则需要使用
`cp -r dir1/. dir2`
如果这时使用`cp -r dir1 dir2`,则也会将`dir1`目录复制到`dir2`中，明显不符合要求。
ps:dir1、dir2改成对应的目录路径即可。

`cp -r /home/www/xxx/statics/. /home/www/statics`
如果存在文件需要先删除
`rm -rf /home/www/statics/*`
否则会一个个文件提示你确认，使用`cp -rf` 也一样提示