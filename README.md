# 多应用Monorepo框架

### 目录结构

```bash
├── package.json
├── packages
│   ├── app-1
│   ├── app-2
│   ├── components
│   └── utils
├── pnpm-lock.yaml
├── pnpm-workspace.yaml
```

1. `packages/app-*`是实际应用，可以替换和新建；
2. `packages/components`是公共组件；
3. `packages/utils`是公共库方法；

### 创建一个子应用

 创建的应用名建议以`@mapps` 为前缀(scope)，进入packages 目录

```shell
$ cd packages
```

使用vite创建应用

```shell
$ pnpm create vite
```

使用vue-cli创建应用

```shell
$ vue create @mapps/xxx
```

也可以使用其他方式创建非vue的应用

```shell
$ npx create-react-app @mapps/xxx
```

### 修改package script

将`app-*`替换成你的应用名（使用`-F/--filter`）或者目录名(使用`-C`)。

```json
  "scripts": {
    "dev:app1": "pnpm run -C packages/app-1 dev",
    "dev:app2": "pnpm run -C packages/app-2 dev",
    "build:app1": "pnpm run -C packages/app-1 build",
    "build:app2": "pnpm run -C packages/app-2 build",
    "dev:mapps":"pnpm -r --filter @mapps/* run dev",
    "build:mapps":"pnpm -r --filter @mapps/* run build",
    "preview": "vite preview"
  },
```

