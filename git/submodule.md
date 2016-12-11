## 子模块的使用

### 创建子模块
```
git submodule add git://github.com/Someone/SomeRepo.git
```

创建完成后，会生成.gitmodules文件
```
cat .gitmodule
[submodule "SomeRepo"]
      path = SomeRepo
      url = git://github.com/Someone/SomeRepo.git
```

### 更新子模块
```
git submodule update
```
本质上，子模块和父项目是不同的仓库。这里有个坑。
git pull并不会更新子模块，此时执行git status发现子模块有更新，则需要执行 git submodule update.
所以正确的更新方式是
```
1. git pull
2. git submodule update
```

### 修改子模块
默认情况下，进入子模块HEAD是处理游离状态(detached HEAD), 所以如果要更新子模块，就先要checkout到master
```
1. cd submodule_folder
2. git checkout master
3. do some mod
4. git add files
5. git commit -m 'Mod submodule'
6. git push
```
如果开始一开始忘记checkout到master并且有进行commit, 则可以采用如下办法
```
1. mod submodule files and commited
2. git log 查看commit hash id 假定id是12345
3. git checkout master
4. git cherry-pick 12345
5. git push
```
