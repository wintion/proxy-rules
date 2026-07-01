# iOS 配置教程

适用设备：iPhone / iPad。

使用 App：Stash。

开始前，请先向维护者拿到：

| 信息 | 填到哪里 |
| --- | --- |
| 服务器地址 | `server` |
| 密码 | `password` |

不要把服务器地址和密码发到群里，也不要发给无关人员。

## 一、安装 Stash

Stash 需要在美区等非中国区 Apple App Store 下载。如果当前 App Store 搜不到，
请切换到美国区等非中国区 Apple ID 后再搜索安装。

在 App Store 搜索并安装：

```text
Stash
```

Stash 是付费 App。安装完成后先打开一次。

## 二、下载配置

打开 Stash：

1. 点底部 `设置`。
2. 进入 `配置文件`。
3. 在 `导入` 里点 `从 URL 下载`。
4. 粘贴这个链接：

```text
https://cdn.jsdelivr.net/gh/wintion/proxy-rules@main/ios/public.yaml
```

5. 点 `下载`。
6. 下载完成后，在 `配置列表` 里选中刚下载的 `public` 配置。

如果上面的链接下载失败，再试这个备用链接：

```text
https://raw.githubusercontent.com/wintion/proxy-rules/refs/heads/main/ios/public.yaml
```

## 三、创建副本并填写信息

还在 Stash 的 `设置` -> `配置文件` 页面：

1. 确认选中了刚下载的 `public` 配置。
2. 点下面 `编辑` 区域里的 `编辑`。
3. 如果弹出提示“订阅的配置可能会被自动更新覆盖”，一定选择 `创建副本`。
4. 不要点 `继续` 直接编辑原始配置。
5. 在新创建的副本里，找到 `My-Trojan` 下面的 `server` 和 `password`。
6. 用维护者给你的信息替换这两个字段。

<font color="red">只允许修改 server 和 password，任何其他参数不要随意改动。</font>

| 字段 | 填什么 |
| --- | --- |
| `server` | 维护者给你的服务器地址 |
| `password` | 维护者给你的密码 |

创建副本后，配置名可能显示为：

```text
public - copy
```

保存后回到配置列表，确认选中的是这个副本，不是原始 `public` 配置。

## 四、开启使用

回到 Stash 首页，打开连接开关。

第一次开启时，iPhone 会提示添加 VPN 配置。选择允许，并输入锁屏密码或
Face ID。

## 五、测试

打开 Safari 访问：

```text
https://www.google.com
```

能打开就说明配置成功。

如果打不开，按顺序检查：

1. Stash 是否已经打开连接开关。
2. `设置` -> `配置文件` 里是否选中了 `public - copy` 这个副本。
3. `server` 和 `password` 是否填错。
4. 手机是否能正常上网。
5. 仍然不行的话，重启手机后再打开 Stash 试试。

## 六、以后怎么改

以后如果维护者更换服务器或密码，只回到：

```text
设置 -> 配置文件 -> 选中 public - copy -> 编辑
```

然后只修改 `server` 和 `password`。

不要去刷新或编辑原始 `public` 配置，避免把已经填好的内容覆盖掉。

[返回目录](../README.md)
