
Git还原操作(revert)

```
回到干净的版本
git reset --hard HEAD

需要还原的版本
git reset <id>
把指针指向前面的HEAD
git reset --soft HEAD@{1}
git commit -m 'Revert to <id>'

```
