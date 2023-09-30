查看工作区状态：

```java
git status
```

将所有文件提交到暂存区

```
git add -A
```

将暂存区的文件提交到本地仓库

```java
git commit -m ‘first commit’
```

将本地仓库提交到远程仓库

```java
git push origin master
```

如果本地仓库中部分文件删除，导致远程仓库和本地仓库代码不一致

```
git pull -rebase ori
```

