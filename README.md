# OpenMap-cn

OpenMap 简体中文汉化版，基于上游 **v0.7.5-beta**。

OpenMap 把魔兽世界的所有区域拼接成一张无缝世界地图：从一个区域缩小即可进入下一个区域，暴雪的
地图、任务日志和 Questie 照常工作。

## 上游项目

| 用途 | 地址 |
| --- | --- |
| 发布页（CurseForge），取新版 | <https://www.curseforge.com/wow/addons/openmap> |
| 原作者 GitHub 仓库 | <https://github.com/jiforever/wowforever-openmap> —— **已无法访问（404）** |
| 非官方镜像（v0.4.0-beta 的最后公开状态） | <https://github.com/fitzforge/wowforever-openmap> |

作者 `jiforever` 的 GitHub 账号与仓库都已下线，插件内的 `Map/News.lua` 也因此把官网指向 CurseForge
而不是 GitHub。所以目前**没有可用的官方 GitHub 上游**：新版本请从 CurseForge 获取，历史代码可参考上面
的镜像（它停在 v0.4.0-beta，不包含 0.7.x，也不接受维护）。若作者恢复仓库，以作者仓库为准。

## 本汉化版做了什么

在保留上游代码与数据的前提下，为**副本内部地图名称**和 **BOSS 名称**提供中文显示：

- `NameCN.lua`：一张只用于显示的译名表（353 条），以及查询函数 `ns.CN(name)`；
- `OpenMap.toc`：加载 `NameCN.lua`，使其先于地图模块加载；
- `Map/Dungeons.lua`：楼层名、分区（wing）名、副本名、副本卡片标题、BOSS 列表与鼠标提示等
  11 处显示点用 `ns.CN()` 包装；
- `Map/Nav.lua`：导航搜索里的副本 / 团队副本条目使用中文名。

译名只作用于界面显示，数据层仍然是游戏原始的英文名。这一点很重要：英文名被用于匹配客户端的
`WING_FLOORS`、入口查询、传给其他插件（NeedRoll、`API.lua` 的 Info）以及查询 Questie 的资料库，
替换成中文会破坏这些功能。

其余界面文本（选项、提示、消息等）由上游自带的 `Locales\zhCN.lua` 提供，本汉化版未改动。

## 安装

将本目录放到 `World of Warcraft\_classic_era_\Interface\AddOns\OpenMap`，或在发布包中保持文件夹名为
`OpenMap`。客户端语言为简体中文时自动生效。

## 同步上游新版本

从 CurseForge 下载新版后，汉化改动只集中在上面列出的 3 个文件（外加 `NameCN.lua`，上游已自带该文件但未加载）。
升级时把新版文件覆盖进来，再按同样方式接入 `ns.CN()` 即可，其余文件应与上游保持一致。

## 许可

代码遵循上游的 MIT 许可（见 `LICENSE.txt`），原作者为 jiforever 与 OpenMap contributors，地图美术资源
版权归暴雪所有。
