# macOS 配置教程

适用设备：Mac 电脑。

使用 App：Clash Verge Rev。

开始前，请先向维护者拿到节点文件，文件名必须叫：

```text
personal.yaml
```

不要把这个文件发到群里，也不要发给无关人员。

## 一、安装 Clash Verge Rev

打开下载页：

```text
https://github.com/clash-verge-rev/clash-verge-rev/releases
```

选择最上面的最新版本，在 `Assets` 里下载：

| Mac 类型 | 下载什么 |
| --- | --- |
| Apple 芯片，M1/M2/M3/M4 | 名字里带 `aarch64` 或 `arm64` 的 `.dmg` |
| Intel 芯片 | 名字里带 `x64` 的 `.dmg` |

不要下载 `Source code`，那个不是安装包。

下载完成后正常安装。安装完成后，先打开一次 Clash Verge Rev。

如果 Mac 提示无法打开，可以右键点击 App，选择 `打开`，再确认一次。

## 二、放入节点文件

1. 打开 Finder。
2. 顶部菜单点 `前往` -> `前往文件夹...`。
3. 粘贴下面这段路径并回车：

```text
~/Library/Application Support/io.github.clash-verge-rev.clash-verge-rev
```

4. 新建一个文件夹，名字必须叫：

```text
proxy_providers
```

5. 把维护者给你的 `personal.yaml` 放进这个文件夹。

注意：文件名必须是 `personal.yaml`，不要变成 `personal.yaml.txt`。

## 三、导入配置

回到 Clash Verge Rev：

1. 打开 `Profiles` 或 `配置` 页面。
2. 点击新增、导入或右上角 `+`。
3. 选择远程订阅，也就是 `Remote`。
4. 粘贴这个链接：

```text
https://cdn.jsdelivr.net/gh/wintion/proxy-rules@main/pc/public.yaml
```

5. 名字可以填：

```text
Proxy Rules
```

6. 保存后，选中这份配置，点击 `Use` 或 `使用`。

如果上面的链接导入失败，再试这个备用链接：

```text
https://raw.githubusercontent.com/wintion/proxy-rules/main/pc/public.yaml
```

## 四、开启使用

进入 Clash Verge Rev 的设置页面：

1. 打开 `System Proxy`，中文界面可能叫 `系统代理`。
2. 模式选择 `Rule`，中文界面可能叫 `规则`。

一般只需要打开系统代理，不要随意改其它设置。

## 五、测试

打开浏览器访问：

```text
https://www.google.com
```

能打开就说明配置成功。

如果打不开，按顺序检查：

1. Clash Verge Rev 是否正在运行。
2. 当前配置是否已经点击 `Use` 或 `使用`。
3. `System Proxy` / `系统代理` 是否已经打开。
4. `personal.yaml` 文件名是否正确。
5. `personal.yaml` 是否放在 `proxy_providers` 文件夹里。
6. 仍然不行的话，重启电脑后再打开 Clash Verge Rev 试试。

## 六、以后怎么改

如果维护者更换服务器或密码，会重新发你 `personal.yaml`。

你只需要替换本机的 `personal.yaml` 文件，然后回到 Clash Verge Rev 重新点击
`Use` / `使用`。

[返回目录](../README.md)
