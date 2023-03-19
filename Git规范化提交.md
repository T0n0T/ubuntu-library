#### Commitizen
提到`git`的规范提交，一般会建议使用`CLI`工具`commitizen`

- 方法一：命令行
```js
// 1. 安装 
commitizen npm install commitizen -D 
// 2. 安装和初始化 
cz-conventional-changelog npx commitizen init cz-conventional-changelog --save-dev --save-exact
// 3. 对当前git仓库增加cz命令
git add .

```

- 方法二：`vscode`插件
![[Pasted image 20230319003118.png]]

![[Pasted image 20230319002145.png]]
