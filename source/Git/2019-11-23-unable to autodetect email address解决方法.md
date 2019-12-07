# unable to auto-detect email address解决方法

 git pull 失败 ,提示：`fatal: refusing to merge unrelated histories` 

 使用

```
git pull origin master --allow-unrelated-histories 
```

然后git提示`unable to auto-detect email address`,

* 在`.git`文件夹下, `vi config`

* 在最前面加上

  ```
  [user]
  email=your email
  name=your name
  ```

* 不需要单引号

