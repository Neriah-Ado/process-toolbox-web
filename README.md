# process-toolbox-web

[工艺工具箱 Process Toolbox](https://github.com/Neriah-Ado/process-toolbox)（私有仓库）的**网页发布仓库**：刻蚀选择比计算器。

## 在线访问

<https://neriah-ado.github.io/process-toolbox-web/>

## 功能

刻蚀选择比（selectivity, S = ER(film) / ER(mask)）计算器，四种模式与私有仓库中的技能 `etch-selectivity-calc`（scripts/selectivity.py）保持同一套算法：

1. **速率法**：由两个刻蚀速率求选择比
2. **损失法**：由同一步刻蚀的厚度损失（或刻蚀前后绝对厚度）求选择比与速率
3. **余量校核**：校核掩膜（光刻胶/硬掩膜）能否撑过规划刻蚀 + 过刻蚀，含掩膜消耗可视化
4. **最小选择比**：反推给定过刻蚀与掩膜损耗预算下所需的 S_min

另附常见刻蚀体系选择比量级参考表（文献量级，仅作 sanity check，不构成工艺规范）。

## 自动部署

push 到 `main` 后由 GitHub Actions（`.github/workflows/deploy-pages.yml`）自动发布到 GitHub Pages，也可在 Actions 页手动触发（workflow_dispatch）。

> 为什么单独建这个仓库：process-toolbox 为私有仓库且账号为 Free 计划，GitHub Pages 不支持私有仓库；此公开仓库仅包含通用计算器页面与文献量级数据，不含任何工艺敏感信息。

## 技术说明

纯静态单文件页面（HTML + CSS + 原生 JS），无任何依赖、无构建步骤、无数据上传（全部计算在浏览器本地完成）。支持 nm / Å / µm 与 min / s 单位切换。
