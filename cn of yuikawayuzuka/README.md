# cn of yuikawayuzuka — KSP 模组汉化补丁

为 KSP 1.12.5 环境中 **尚未被汉化** 的模组提供简体中文文本的独立汉化模组。
与 `0000Tinygrox_CNPatches` 互补，不重复其已覆盖内容。

- **目标游戏**：KSP 1（1.12.5）
- **安装位置**：`GameData/cn of yuikawayuzuka/`
- **依赖**：无强制依赖（纯 Localization，不需要 ModuleManager）
- **翻译规则**：见 [`术语规范.md`](术语规范.md)，翻译前必读

---

## ⚠️ 安装前必读：语言设置

KSP 只有在语言设为 **简体中文** 时才会加载 `zh-cn` 文本。
检查 `KSP/settings.cfg`：

```
LANGUAGE = zh-cn
```

若为 `LANGUAGE = en-us`，请在游戏内 `设置 → 通用 → 语言` 切换为「简体中文」。
**否则本模组及任何汉化包都不会生效。**

---

## 工作原理

KSP 会全局注册所有 `Localization` 节点中的键值。本模组不修改任何原模组文件，
只在独立目录中声明 `zh-cn` 的键值，由游戏本地化系统接管显示。

因此：

- 不会覆盖或破坏原模组文件，可随时删除还原。
- 不同模组间的键名冲突会互相覆盖（后加载者生效），故本模组对所有键名做了逐一对账。
- 纯文本替换，**不影响存档**，不需要备份存档。

---

## 进度

### ✅ 已完成

| 模组 | 键数 | 说明 |
|---|---:|---|
| MunksFixes | 77 | VAB 分类名、Waterfall 尾焰名、燃料切换 |
| KerbalEngineer | 8 | ER-7500 / 工程系统部件名与描述 |
| BackgroundResourceProcessing | 39 | 资源显示名、加载提示 |
| NavyFish (DPAI) | 27 | 对接口对齐指示器设置界面 |
| SpaceTuxLibrary | 18 | 按钮管理器、取色器 |
| Benjee10_sharedAssets | 6 | VABOrganizer 子分类 |

### 📋 待办（真实缺口，共 101 个模组）

按玩家可见度排序的优先梯队：

**第一梯队 —— 界面/信息类，改动收益最高**

| 模组 | 待译键数 |
|---|---:|
| EditorExtensionsRedux | 164 |
| VABOrganizer | 139 |
| DockingCamKURS | 123 |
| KerbalColonies | 288 |
| OuterParallax | 61 |
| KSPWheel / KSP-AVC / ToolbarControl 等 | 少量 |

**第二梯队 —— 科学文本类（注意剧透属性）**

| 模组 | 待译键数 |
|---|---:|
| OPM | 2313 |
| DMagicUtilities | 384 |
| OuterParallax 科学段落 | — |

**第三梯队 —— 未提供本地化接口，需补丁注入**

`Scatterer`、`EVE`、`ParallaxContinued`、`Waterfall`、`TUFX`、`kOS`、
`Firespitter`、`HabTech2`、`KIS`、`KAS`、`KerbalKonstructs`、`WaypointManager`、
`BetterTimeWarp`、`DistantObject`、`RCSBuildAid`、`ShipManifest` 等约 80 个模组。

> 这些模组自身没有 `Localization` 节点，文本多硬编码在 DLL 或写在
> `PART`/`MODULE` 的 `title`/`description` 字段中。需要用 ModuleManager
> 补丁逐个替换，工作方式与第一、二梯队不同，将单独成批处理。

---

## 翻译约定

总原则：**缩写保留，专有名词看情况，描述性名词照译。**
完整规则与译名表见 [`术语规范.md`](术语规范.md)。

1. **保留原文**：缩写（`EVA`/`RCS`/`DPAI`/`TAC`）、模组名（`Endurance`/`Benjee10`）、
   星球名（`Kerbin`/`Jool`/`Tekto`）、单位标记（`v`/`y`/`d`/`h`/`m`/`s`）。
2. **必须汉化**：描述性专业名词（`Kerolox`→煤油液氧、`Metal`→金属、`RocketParts`→火箭零件）。
3. **零件名照抄官方译名**：`Terrier`→猎犬、`Twitch`→开关、`Thud`→砰砰、`Poodle`→贵宾犬。
   **不可自创**，须查 `Squad/Localization/dictionary.cfg` 确认。
4. **不修改**键名、占位符（`<<1>>`）、富文本标签（`<color=...>`）、转义符（`\n`、`\"`）与注释。
5. 中文与英文/数字之间加空格（如「5m 隔热罩」「128 位」）。
6. 全部文件使用 **UTF-8** 编码。
7. 翻译第三方模组文本前确认其许可证允许再分发译文。

---

## 目录结构

```
GameData/
└── YuikawaCNPatches/
    ├── README.md
    ├── YuikawaCNPatches.version
    └── Localization/
        ├── BackgroundResourceProcessing.cfg
        ├── Benjee10_sharedAssets.cfg
        ├── KerbalEngineer.cfg
        ├── MunksFixes.cfg
        ├── NavyFish_DPAI.cfg
        └── SpaceTuxLibrary.cfg
```

新增模组时，在 `Localization/` 下按 `<模组名>.cfg` 建立文件即可，无需其他配置。

---

## 卸载

删除 `GameData/YuikawaCNPatches/` 整个文件夹。

---

## 排错

**中文没有出现？**

1. 确认 `settings.cfg` 中 `LANGUAGE = zh-cn`。
2. 确认没有其他汉化包用相同键名覆盖（本模组键名已逐一对账，冲突仅可能来自外部）。
3. 查看 `KSP.log` 中是否有 `Localization` 相关报错。
4. 检查 `ModuleManager.ConfigErrors`（仅当使用 MM 补丁时）。

**部分文本仍是英文？** 说明该键尚未翻译，属于待办范围，可对照上表补全。
