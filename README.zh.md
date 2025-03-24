# 🎭 Playwright

[![npm version](https://img.shields.io/npm/v/playwright.svg)](https://www.npmjs.com/package/playwright) <!-- GEN:chromium-version-badge -->[![Chromium version](https://img.shields.io/badge/chromium-135.0.7049.28-blue.svg?logo=google-chrome)](https://www.chromium.org/Home)<!-- GEN:stop --> <!-- GEN:firefox-version-badge -->[![Firefox version](https://img.shields.io/badge/firefox-136.0-blue.svg?logo=firefoxbrowser)](https://www.mozilla.org/en-US/firefox/new/)<!-- GEN:stop --> <!-- GEN:webkit-version-badge -->[![WebKit version](https://img.shields.io/badge/webkit-18.4-blue.svg?logo=safari)](https://webkit.org/)<!-- GEN:stop --> [![加入 Discord](https://img.shields.io/badge/join-discord-infomational)](https://aka.ms/playwright/discord)

## [文档](https://playwright.dev) | [API 参考](./docs/src.zh/api/class-playwright)

Playwright 是一个用于 Web 测试和自动化的框架。它允许使用单一 API 测试 [Chromium](https://www.chromium.org/Home)、[Firefox](https://www.mozilla.org/en-US/firefox/new/) 和 [WebKit](https://webkit.org/)。Playwright 旨在实现跨浏览器的 Web 自动化，具有**常青特性**、**功能强大**、**可靠稳定**和**执行迅速**的特点。

|          | Linux | macOS | Windows |
|   :---   | :---: | :---: | :---:   |
| Chromium <!-- GEN:chromium-version -->135.0.7049.28<!-- GEN:stop --> | :white_check_mark: | :white_check_mark: | :white_check_mark: |
| WebKit <!-- GEN:webkit-version -->18.4<!-- GEN:stop --> | :white_check_mark: | :white_check_mark: | :white_check_mark: |
| Firefox <!-- GEN:firefox-version -->136.0<!-- GEN:stop --> | :white_check_mark: | :white_check_mark: | :white_check_mark: |

所有平台上的所有浏览器均支持无头执行。查看[系统要求](./docs/src.zh/intro#system-requirements)了解详情。

寻找 [Python](https://playwright.dev/python/docs/intro)、[.NET](https://playwright.dev/dotnet/docs/intro) 或 [Java](https://playwright.dev/java/docs/intro) 版本的 Playwright？

## 安装

Playwright 拥有自己的端到端测试运行器，我们称之为 Playwright Test。

### 使用初始化命令

开始使用 Playwright Test 最简单的方法是运行 init 命令。

```Shell
# 在项目根目录运行
npm init playwright@latest
# 或创建新项目
npm init playwright@latest new-project
```

这将创建一个配置文件，可选择添加示例、GitHub Action 工作流和第一个测试 example.spec.ts。现在您可以直接跳转到编写断言部分。

### 手动安装

添加依赖并安装浏览器。

```Shell
npm i -D @playwright/test
# 安装支持的浏览器
npx playwright install
```

您可以选择只安装选定的浏览器，详情请参阅[安装浏览器](./docs/src.zh/cli#install-browsers)。或者您可以完全不安装浏览器而使用现有的[浏览器通道](./docs/src.zh/browsers)。

* [入门指南](./docs/src.zh/intro)
* [API 参考](./docs/src.zh/api/class-playwright)

## 功能特性

### 强大可靠 • 无不稳定测试

**自动等待**。Playwright 在执行操作前会等待元素变为可操作状态。它还具有丰富的检查事件集。这两者的结合消除了对人为超时的需求——不稳定测试的主要原因。

**Web 优先断言**。Playwright 断言专为动态 Web 创建。检查会自动重试，直到满足必要条件。

**跟踪**。配置测试重试策略，捕获执行跟踪、视频和截图以消除不稳定性。

### 无需取舍 • 无限制

浏览器在不同进程中运行属于不同源的 Web 内容。Playwright 与现代浏览器架构保持一致，并在进程外运行测试。这使 Playwright 不受典型进程内测试运行器限制的影响。

**多元化测试**。测试跨越多个标签页、多个源和多个用户的场景。为不同用户创建具有不同上下文的场景，并在一个测试中针对服务器运行它们。

**可信事件**。悬停元素、与动态控件交互并产生可信事件。Playwright 使用与真实用户无法区分的真实浏览器输入管道。

测试框架，穿透 Shadow DOM。Playwright 选择器能穿透 shadow DOM 并允许无缝进入框架。

### 完全隔离 • 快速执行

**浏览器上下文**。Playwright 为每个测试创建一个浏览器上下文。浏览器上下文相当于全新的浏览器配置文件。这提供了零开销的完全测试隔离。创建新的浏览器上下文仅需几毫秒。

**一次登录**。保存上下文的身份验证状态并在所有测试中重用它。这绕过了每个测试中重复的登录操作，同时提供了独立测试的完全隔离。

### 强大工具

**[代码生成](./docs/src.zh/codegen)**。通过记录您的操作生成测试。将它们保存为任何语言。

**[Playwright 检查器](./docs/src.zh/inspector)**。检查页面、生成选择器、逐步执行测试、查看点击点并探索执行日志。

**[跟踪查看器](./docs/src.zh/trace-viewer)**。捕获所有信息以调查测试失败。Playwright 跟踪包含测试执行屏幕录制、实时 DOM 快照、操作浏览器、测试源码等。

寻找适用于 [TypeScript](./docs/src.zh/intro)、[JavaScript](./docs/src.zh/intro)、[Python](https://playwright.dev/python/docs/intro)、[.NET](https://playwright.dev/dotnet/docs/intro) 或 [Java](https://playwright.dev/java/docs/intro) 的 Playwright？

## 示例

要了解如何运行这些 Playwright Test 示例，请查看我们的[入门文档](./docs/src.zh/intro)。

#### 页面截图

此代码片段导航到 Playwright 主页并保存截图。

```TypeScript
import { test } from '@playwright/test';

test('页面截图', async ({ page }) => {
  await page.goto('https://playwright.dev/');
  await page.screenshot({ path: `example.png` });
});
```

#### 移动设备和地理位置

此片段在指定地理位置模拟设备上的 Mobile Safari，导航到 maps.google.com，执行操作并截图。

```TypeScript
import { test, devices } from '@playwright/test';

test.use({
  ...devices['iPhone 13 Pro'],
  locale: 'en-US',
  geolocation: { longitude: 12.492507, latitude: 41.889938 },
  permissions: ['geolocation'],
})

test('移动设备和地理位置', async ({ page }) => {
  await page.goto('https://maps.google.com');
  await page.getByText('Your location').click();
  await page.waitForRequest(/.*preview\/pwa/);
  await page.screenshot({ path: 'colosseum-iphone.png' });
});
```

#### 在浏览器上下文中求值

此代码片段导航到 example.com，并在页面上下文中执行脚本。

```TypeScript
import { test } from '@playwright/test';

test('在浏览器上下文中求值', async ({ page }) => {
  await page.goto('https://www.example.com/');
  const dimensions = await page.evaluate(() => {
    return {
      width: document.documentElement.clientWidth,
      height: document.documentElement.clientHeight,
      deviceScaleFactor: window.devicePixelRatio
    }
  });
  console.log(dimensions);
});
```

#### 拦截网络请求

此代码片段设置页面的请求路由，以记录所有网络请求。

```TypeScript
import { test } from '@playwright/test';

test('拦截网络请求', async ({ page }) => {
  // 记录并继续所有网络请求
  await page.route('**', route => {
    console.log(route.request().url());
    route.continue();
  });
  await page.goto('http://todomvc.com');
});
```

## 资源

* [文档](https://playwright.dev)
* [API 参考](./docs/src.zh/api/class-playwright/)
* [贡献指南](CONTRIBUTING.md)
* [更新日志](https://github.com/microsoft/playwright/releases) 