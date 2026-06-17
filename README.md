# Proxy Rules 使用说明

这是一份公共代理规则配置。

目前分两套使用方式：

| 设备 | 推荐客户端 | 配置方式 |
| --- | --- | --- |
| 电脑，macOS / Windows | Clash Verge Rev | 订阅公开配置 `pc/public.yaml`，本机放节点文件 |
| 手机，iPhone / iPad | Stash | 订阅公开配置 `ios/public.yaml`，在 App 里修改示例节点 |

规则文件可以公开放在 GitHub。节点地址、密码、订阅 token 不会写到 GitHub
里。

电脑端使用时只需要做两件事：

1. 订阅这个公共规则链接。
2. 把自己的节点信息放到本机。

手机端使用时订阅公开配置，再把示例节点改成真实节点。以后只更新远程规则
集，不刷新主配置。

## 电脑端：Clash Verge Rev

### 一、准备信息

开始之前，先向维护者拿到你的节点信息。通常长这样：

```yaml
proxies:
  - name: My-Trojan
    type: trojan
    server: 更改这里
    port: 443
    password: 更改这里
    sni:
    skip-cert-verify: false
    udp: true
```

维护者会私下发给你真实内容。不要把真实节点信息发到群里，也不要上传到
GitHub。

### 二、下载安装 Clash Verge Rev

打开 Clash Verge Rev 的 GitHub 下载页：

```text
https://github.com/clash-verge-rev/clash-verge-rev/releases
```

选择最上面的最新版本，在 `Assets` 区域下载适合自己电脑的安装包：

| 电脑类型 | 下载什么 |
| --- | --- |
| Mac，Apple 芯片，M1/M2/M3/M4 | 下载名字里带 `aarch64` 或 `arm64` 的 `.dmg` |
| Mac，Intel 芯片 | 下载名字里带 `x64` 的 `.dmg` |
| Windows 普通电脑 | 下载名字里带 `x64` 的 `.exe` |

不要下载 `Source code`，那个不是安装包。

下载完成后正常安装。Mac 如果提示无法打开，可以右键点击 App，选择
`打开`，再确认一次。

### 三、先启动一次 Clash Verge

安装后先打开一次 Clash Verge Rev。

这一步很重要，因为它会自动创建配置目录。打开后不用急着导入订阅，先继续
下一步。

### 四、放入你的节点文件

Clash Verge 需要在本机找到一个叫 `personal.yaml` 的文件。这个文件里放你
自己的节点信息。

### macOS

1. 打开 Finder。
2. 顶部菜单选择 `前往` -> `前往文件夹...`。
3. 粘贴下面这段路径，然后回车：

```text
~/Library/Application Support/io.github.clash-verge-rev.clash-verge-rev
```

4. 在打开的文件夹里，新建一个文件夹，名字必须是：

```text
proxy_providers
```

5. 进入 `proxy_providers` 文件夹。
6. 新建一个文件，名字必须是：

```text
personal.yaml
```

7. 把维护者私下发给你的节点内容粘贴进去，保存。

最后文件位置应该是：

```text
~/Library/Application Support/io.github.clash-verge-rev.clash-verge-rev/proxy_providers/personal.yaml
```

### Windows

1. 打开文件资源管理器。
2. 在地址栏粘贴下面这段路径，然后回车：

```text
%APPDATA%\io.github.clash-verge-rev.clash-verge-rev
```

3. 在打开的文件夹里，新建一个文件夹，名字必须是：

```text
proxy_providers
```

4. 进入 `proxy_providers` 文件夹。
5. 新建一个文件，名字必须是：

```text
personal.yaml
```

6. 把维护者私下发给你的节点内容粘贴进去，保存。

最后文件位置应该是：

```text
%APPDATA%\io.github.clash-verge-rev.clash-verge-rev\proxy_providers\personal.yaml
```

注意：文件名必须是 `personal.yaml`，不要变成
`personal.yaml.txt`。

### 五、导入公共规则订阅

回到 Clash Verge Rev。

1. 打开左侧 `Profiles` 或 `配置` 页面。
2. 点击新增、导入或右上角的 `+`。
3. 选择远程订阅，也就是 `Remote`。
4. 粘贴下面这个订阅链接：

```text
https://cdn.jsdelivr.net/gh/wintion/proxy-rules@main/pc/public.yaml
```

5. 名字可以填：

```text
Proxy Rules
```

6. 保存或导入。
7. 选中刚导入的配置，点击 `Use` 或 `使用`。

如果 CDN 链接无法导入，可以改用这个备用链接：

```text
https://raw.githubusercontent.com/wintion/proxy-rules/main/pc/public.yaml
```

### 六、打开代理

进入 Clash Verge Rev 的设置页面：

1. 开启 `System Proxy`，中文界面可能叫 `系统代理`。
2. 模式选择 `Rule`，中文界面可能叫 `规则`。
3. 如果你希望所有 App 都走 Clash，可以开启 `TUN Mode`，中文界面可能叫
   `TUN 模式`。第一次开启时，系统可能会要求输入电脑密码或允许网络扩展。

普通网页访问一般开启 `System Proxy` 就够了。某些 App 不听系统代理时，再
开启 `TUN Mode`。

### 七、选择节点

打开左侧 `Proxies` 或 `代理` 页面。

你会看到这些分组：

| 分组 | 怎么选 |
| --- | --- |
| `Proxy` | 选 `Auto`，或者手动选一个具体节点 |
| `Auto` | 自动选择测速较快的节点 |
| `Final` | 保持默认即可 |

一般只需要把 `Proxy` 设置成 `Auto`。

如果 `Proxy` 里看不到任何节点，通常是第四步的 `personal.yaml` 没放对，或
文件名写错了。

### 八、测试是否成功

打开浏览器测试：

```text
https://www.google.com
```

如果能打开，说明基本配置成功。

如果打不开，按下面顺序检查：

1. Clash Verge 是否正在运行。
2. 当前配置是否已经点击 `Use` 或 `使用`。
3. 模式是否是 `Rule` / `规则`。
4. `System Proxy` / `系统代理` 是否打开。
5. `Proxy` 分组里是否有节点，并且不是 `DIRECT`。
6. `personal.yaml` 文件名是否正确，位置是否正确。

### 九、以后怎么更新规则

以后维护者更新 GitHub 规则后，你不需要重新填写节点。

你只需要在 Clash Verge 的 `Profiles` / `配置` 页面，找到 `Proxy Rules`，
点击刷新按钮即可。

如果只是维护者更换了你的节点密码或服务器地址，维护者会私下发你新的节点
内容。你只需要更新本机的 `personal.yaml` 文件，然后回到 Clash Verge 重新
点击 `Use` / `使用`。

## 手机端：iPhone / iPad 使用 Stash

手机端推荐使用 Stash。

手机端只订阅一个公共配置。公共配置里有一个示例节点，订阅后把这个示例节点
改成维护者私下告诉你的真实节点。

以后维护规则时，只更新 `ios/rules/*.yaml`。这些规则通过 Stash 的
`rule-providers` 自动刷新，不需要刷新 `ios/public.yaml` 主配置。

注意：不要手动刷新 Stash 里的 `Proxy Rules iOS` 主配置，否则示例节点可能
覆盖你已经改好的真实节点。

### 一、下载安装 Stash

在 App Store 搜索并安装：

```text
Stash
```

Stash 是付费 App。安装完成后先打开一次。

### 二、导入公共规则配置

向维护者索取公共订阅链接，或者直接使用下面这个链接：

```text
https://cdn.jsdelivr.net/gh/wintion/proxy-rules@main/ios/public.yaml
```

打开 Stash：

1. 进入 `Profiles` 或 `配置`。
2. 点击 `+`。
3. 选择从 URL 下载配置。
4. 粘贴上面的订阅链接。
5. 名字可以填：

```text
Proxy Rules iOS
```

6. 保存，并选中这份配置。

如果 CDN 链接无法导入，可以改用这个备用链接：

```text
https://raw.githubusercontent.com/wintion/proxy-rules/refs/heads/main/ios/public.yaml
```

### 三、修改示例节点

公共配置导入后，里面会有一个示例节点：

```text
My-Trojan
```

把这个节点改成维护者私下告诉你的真实节点信息：

| 字段 | 填什么 |
| --- | --- |
| `name` | 节点名字，可以不改 |
| `server` | 服务器地址 |
| `port` | 端口 |
| `password` | 密码 |
| `sni` | 如果维护者没特别说明，就留空 |

不要把真实节点信息发到群里，也不要上传到 GitHub。

### 四、选择节点

进入 Stash 的 `Proxy` 或 `代理` 页面。

你会看到这些分组：

| 分组 | 怎么选 |
| --- | --- |
| `Proxy` | 选 `Auto`，或者手动选一个具体节点 |
| `Auto` | 自动选择测速较快的节点 |
| `Final` | 保持默认即可 |

一般只需要把 `Proxy` 设置成 `Auto`。

如果 `Proxy` 里只有示例节点，或者测试不通，通常是第三步还没有把示例节点
改成真实节点。

### 五、开启 VPN

回到 Stash 首页，打开连接开关。

第一次开启时，iPhone 会提示添加 VPN 配置。选择允许，并输入锁屏密码或
Face ID。

### 六、测试是否成功

打开 Safari 测试：

```text
https://www.google.com
```

如果能打开，说明基本配置成功。

如果打不开，按下面顺序检查：

1. Stash 是否已经开启连接。
2. 当前 profile 是否选中了 `Proxy Rules iOS`。
3. `My-Trojan` 是否已经改成真实节点。
4. `Proxy` 分组里是否有节点，并且不是 `DIRECT`。
5. 手机是否正在使用一个能正常联网的 Wi-Fi 或蜂窝网络。

### 七、以后怎么更新手机规则

维护者更新 GitHub 规则后，你不需要重新填写节点。

Stash 会按照配置里的 `interval` 刷新远程规则集，也就是
`ios/rules/custom-direct.yaml` 和 `ios/rules/custom-proxy.yaml`。

不要手动刷新 `Proxy Rules iOS` 主配置；如果刷新了，节点可能会恢复成示例
值，需要重新填写一次。

如果维护者更换了你的节点密码或服务器地址，会私下告诉你新的节点信息。你
只需要回到 Stash 里修改 `My-Trojan` 节点。

## 给维护者

电脑端日常维护：

| 文件 | 用途 |
| --- | --- |
| `pc/rules/custom-direct.yaml` | 强制直连的域名 |
| `pc/rules/custom-proxy.yaml` | 强制代理的域名 |

手机端日常维护：

| 文件 | 用途 |
| --- | --- |
| `ios/public.yaml` | 手机端 Stash 公共订阅配置，只放示例节点 |
| `ios/rules/custom-direct.yaml` | 手机端强制直连的域名 |
| `ios/rules/custom-proxy.yaml` | 手机端强制代理的域名 |

不要把真实手机端节点写进 `ios/public.yaml`，只保留示例节点。

规则文件格式：

```yaml
payload:
  - '+.example.com'
  - 'exact.example.com'
```

`+.example.com` 表示主域名和所有子域名都匹配。`exact.example.com` 只匹配
这个完整域名。

本仓库不要提交真实节点信息。`.gitignore` 已经忽略了本地私密配置和
`proxy_providers/*.yaml`。

基础 YAML 校验：

```sh
ruby -e 'require "yaml"; Dir["pc/public.yaml", "ios/public.yaml", "pc/rules/*.yaml", "ios/rules/*.yaml"].each { |f| YAML.load_file(f); puts "OK #{f}" }'
```
