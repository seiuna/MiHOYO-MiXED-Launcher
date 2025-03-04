[English Document](/README.md)

# 米家聚合启动器

By HoraceHyy
> 聚合启动米哈游游戏并分析游戏内玩家信息。

# 咕咕咕

最近做别的项目学到了点新知识，顿觉本项目的代码写的依托史，故接下来想浅浅改一下代码，可能更新会很慢，请见谅！

# 功能

- [x] 聚合启动原神、崩坏：星穹铁道、崩坏3rd。
- [ ] 待支持绝区零。
- [x] 手动导入游戏路径。
- [x] 多语言支持。
- [x] 以卡片形式展现原神和崩坏：星穹铁道的游戏内账号信息。
- [x] 保留了官方启动器的所有UI元素。
- [x] 自动计算游戏大版本更新并提醒。

# 截图

<details>
  <summary>点击展开</summary>

- 应用主页，背景图片可自定义 (Pixiv @anna_drw01)

  <img width="500" src="https://github.com/HoraceHuang-ui/MiHOYO-MiXED-Launcher/assets/67905897/93617970-7d3e-43ea-8004-d7fbcbc55452"/>

  <p></p>

- 原神启动页面

  <img width="500" src="https://github.com/HoraceHuang-ui/MiHOYO-MiXED-Launcher/assets/67905897/9434ed2a-fa32-49fa-9ce3-353060e80d81"/>

  <p></p>

- 原神账号数据

  <img width="500" src="https://github.com/HoraceHuang-ui/MiHOYO-MiXED-Launcher/assets/67905897/1a3d48f7-a636-40d4-8272-52d81b0f8069"/>

<p></p>

- 崩坏：星穹铁道启动页面

  <img width="500" src="https://github.com/HoraceHuang-ui/MiHOYO-MiXED-Launcher/assets/67905897/99800c57-707d-4753-bd6d-0783556cd427"/>

<p></p>

- 崩坏：星穹铁道账号数据

  <img width="500" src="https://github.com/HoraceHuang-ui/MiHOYO-MiXED-Launcher/assets/67905897/d366f516-3441-4cb8-8afa-64342982bcd8"/>

</details>

# 注意事项

- 本软件使用 GitHub 域名的 URL 来检测自身更新与获取崩坏：星穹铁道角色信息相关资源。如果您是中国大陆用户，请确保代理网络条件通畅。

# 开发

## 依赖

```
pnpm i
```

## 调试

```
pnpm dev
```

## 构建

```
pnpm build
```

## 提示

- 本程序检测自身更新目前用的是 GitHub
  API，但一旦把含token的代码同步到这里就会自动销毁，所以构建时请自行申请一个token，放在`electron/main/index.ts`
  的`Octokit.auth`中。

```ts
  const {Octokit} = require("@octokit/core")
const octokit = new Octokit({
    auth: "<YOUR TOKEN HERE>"
})
```

- 由于一些原因，在开发和生产环境中某些文件的相对路径可能会改变。在`src/pages/SettingsPage.vue`中，`package.json`的相对路径取决于环境。

```ts
  // BUILD: '../../app.asar/package.json'
  // DEV: '../../package.json'
fetch('../../app.asar/package.json')
    .then(response => response.json())
    .then((resp) => {
        appVer.value = resp.version
    })
```

# 鸣谢

- [electron-vite/electron-vite-vue](https://github.com/electron-vite/electron-vite-vue)
- [enkanetwork.js](https://github.com/Jelosus2/enkanetwork.js)
- [Mar-7th/MiHoMo API](https://march7th.xiaohei.moe/zh/resource/mihomo_api.html) | [Mar-7th/StarRailRes](https://github.com/Mar-7th/StarRailRes)

# 翻译

- **English** @HoraceHuang-ui
- **简体中文** @HoraceHuang-ui
- **繁體中文** @HoraceHuang-ui *(需要修改)*
- **日本語** @JonathanKwok
- **Русский** @MCheping8108
- **Français** @MCheping8108

点击下方徽章来帮助参与翻译：

[![Crowdin](https://badges.crowdin.net/mihoyo-mixed-launcher/localized.svg)](https://crowdin.com/project/mihoyo-mixed-launcher)

# 其他

- `electron-store` 存储条目备忘：
    - `targetVersion` 算上忽略更新后的（伪）当前版本
    - `mainBgPath` 主页背景图片的`base64`
    - `dialogStyle` 非游戏界面的弹窗样式
    - `gsLauncherPath` 原神官方启动器所在目录
    - `gsGamePath` 原神游戏本体可执行文件的路径
    - `genshinUpd` 原神当前版本已更新
    - `genshinInfo` 原神账号信息
    - `srLauncherPath`
    - `srGamePath`
    - `starRailUpd`
    - `starRailInfo`
    - `hi3LauncherPath`
    - `hi3GamePath`
    - `honkai3Upd`
