# 第三方组件

本站**没有任何构建步骤**，所有依赖都是把文件直接提交进 `assets/vendor/`，
因此下面这份清单就是仓库里实际存在的那些文件，没有「构建时下载」这种
看不到也删不掉的东西。

目录名带版本号（`font-awesome@6.5.1`）是为了让「现在跑的是哪一版」能一眼看出来，
以及让「升级」成为一次能在 diff 里看见的改动。**只升级一个 CSS、不动 woff2**
这种事在这里发生过（见下面 Font Awesome 一节）。

---

## Font Awesome Free 6.5.1

- 文件：`assets/vendor/font-awesome@6.5.1/`
- 主页：https://fontawesome.com
- 许可：**图标** CC BY 4.0（icons 目录的部分）、**字体** SIL OFL 1.1、**代码** MIT
- 本仓库只取了 Free 版里的 Solid / Regular / Brands 三套图标字体与 `all.min.css`

### 一处必须记下来的事故

线上这份 `webfonts/fa-solid-900.woff2` 曾经只有 **1828 字节**（`totalSfntSize=3628`，
约 1% 的字形）。症状是图标全部渲染成豆腐块——CSS 里 `content` 是在的，
class 也挂对了，但字体文件本身是个残缺的子集，另一个仓库（状态站）有完整的
156496 字节那份，两边一对比才看出来。

**教训**：`assets/vendor/` 里的东西是提交进 git 的，不会有人再去校验一遍。
文件小得离谱时它不会自己报警，只会在页面上表现为「图标全没了」。
所以体积本身就是一项检查：任何低于预期一个数量级的 vendor 文件都该被当成故障。

---

## ZCOOL KuaiLe

- 文件：`assets/vendor/fonts/ZCOOL_KuaiLe.css`、`files/ZCOOL_KuaiLe.woff2`
- 来源：Google Fonts
- 许可：SIL Open Font License 1.1
- 改动：原样搬运，未修改字形

## Orbitron

- 文件：`assets/vendor/fonts/Orbitron.css`、`files/Orbitron-500.ttf`、`files/Orbitron-700.ttf`
- 来源：Google Fonts
- 许可：SIL Open Font License 1.1
- 改动：原样搬运，未修改字形。**这两个是 .ttf 而不是 .woff2**——它们是给
  不支持 woff2 的老浏览器留的兜底

---

## 本仓库自有代码

`assets/css/tokens.css`、`assets/css/style.css`、`assets/css/toast.css`、
`assets/js/app.js`、`index.html`、`404.html` 均为本站原创。

`assets/vendor/images/bg.webp`、`assets/vendor/images/bg-portrait.webp` 是自制背景图；
`assets/vendor/hitokoto.json` 是站内自撰的语料（不是 hitokoto.cn 的导出——
那套 API 已经不服务了）。
