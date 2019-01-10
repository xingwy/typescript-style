



##**ReadMe**

- [**TS编码规范**](https://github.com/xingwy/typescript-style/blob/master/docs/TypeScript%E7%BC%96%E7%A0%81%E8%A7%84%E8%8C%83%20%E5%88%9D.md)
- [**TSLint规则**](https://github.com/xingwy/typescript-style/blob/master/docs/tslint.md)

### **ts-style**

tslint使用[google-ts-style](https://github.com/google/ts-style)规则

如果使用npm@5.3+，node 8.3+请运行

```shell
npx gts init
```

如果使用的是旧版，请运行

```shell
npm install --save-dev gts typescript@2.x
```

当你运行npx gts init命令时，它做的事情

- 将自定义`tsconfig.json`文件添加到使用Google TypeScript样式的项目中。
- 将必要的devDependencies添加到您的`package.json`。
- 添加脚本到您的`package.json`
  - `check`：Lints和格式问题检查。
  - `fix`：自动修复格式和linting问题（如果可能）。
  - `clean`：删除输出文件。
  - `compile`：使用TypeScript编译器编译源代码。
  - `pretest`，`posttest`和`prepare`：便利集成

### **格式检查**

```shell
gts check index.ts
gts check one.ts two.ts three.ts
gts check *.ts
```

