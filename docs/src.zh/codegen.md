---
id: codegen
title: "测试生成器"
---

import LiteYouTube from '@site/src/components/LiteYouTube';

## 简介

Playwright 具有在浏览器中执行操作时为您生成测试的能力，这是快速开始测试的绝佳方式。Playwright 会查看您的页面并找出最佳的定位器，优先使用[角色、文本和测试 ID 定位器](./locators.md)。如果生成器发现多个元素匹配定位器，它将改进定位器使其更具韧性，唯一标识目标元素。

## 在 VS Code 中生成测试
* langs: js

安装 VS Code 扩展，直接从 VS Code 生成测试。该扩展可在 [VS Code 市场](https://marketplace.visualstudio.com/items?itemName=ms-playwright.playwright)获取。查看我们关于 [VS Code 入门](./getting-started-vscode.md)的指南。

<LiteYouTube
    id="LM4yqrOzmFE"
    title="在 VS Code 中生成 Playwright 测试"
/>

### 录制新测试

要录制测试，请点击测试侧边栏中的**录制新测试**按钮。这将创建一个 `test-1.spec.ts` 文件并打开一个浏览器窗口。

<img width="1385" alt="在 VS Code 中录制新测试" src="https://user-images.githubusercontent.com/13063165/220961665-615d0ab8-3f0b-439c-ad0b-0424d9aa154b.png" />

在浏览器中，转到您想要测试的 URL，然后开始点击以记录用户操作。

![生成用户操作](https://github.com/microsoft/playwright/assets/13063165/1d4c8f37-8325-4816-a665-d0e95e63f509)

Playwright 将记录您的操作并直接在 VS Code 中生成测试代码。您还可以通过选择工具栏中的一个图标，然后点击页面上的元素来生成断言。可以生成以下断言：
  * `'assert visibility'` 断言元素可见
  * `'assert text'` 断言元素包含特定文本
  * `'assert value'` 断言元素具有特定值

![生成断言](https://github.com/microsoft/playwright/assets/13063165/d131eb35-b2ca-4bf4-a8ac-88b6e40dcf07)

录制完成后，点击**取消**按钮或关闭浏览器窗口。然后，您可以检查您的 `test-1.spec.ts` 文件并根据需要手动改进它。

![生成测试的代码](https://github.com/microsoft/playwright/assets/13063165/2ba4c212-4713-460a-b054-6dc6b67a9a7c)

### 在光标位置录制

要从测试中的特定点开始录制，请将光标移至您想要录制更多操作的位置，然后从测试侧边栏点击**在光标处录制**按钮。如果浏览器窗口尚未打开，请先勾选"显示浏览器"运行测试，然后点击**在光标处录制**按钮。

![在 VS Code 中光标处录制](https://github.com/microsoft/playwright/assets/13063165/77948ab8-92a2-435f-9833-0944da5ae664)

在浏览器窗口中开始执行您想要录制的操作。

<img width="1394" alt="向待办应用添加遛狗项目" src="https://user-images.githubusercontent.com/13063165/220960770-6435cec7-1723-42a8-8c1f-8244e2d800c7.png" />

在 VS Code 的测试文件中，您将看到新生成的操作添加到光标位置的测试中。

![生成测试的代码](https://github.com/microsoft/playwright/assets/13063165/4f4bb34e-9cda-41fe-bf65-8d8016d84c7f)

### 生成定位器

您可以使用测试生成器生成定位器。
- 点击测试侧边栏中的**选择定位器**按钮，然后将鼠标悬停在浏览器窗口中的元素上，查看每个元素下方突出显示的[定位器](./locators.md)。
- 点击您需要的元素，它将显示在 VS Code 中的**选择定位器**框中。
- 按键盘上的 <kbd>Enter</kbd> 键将定位器复制到剪贴板，然后粘贴到代码中的任何位置。或按"Escape"取消。

<img width="1641" alt="在 VS Code 中选择定位器" src="https://user-images.githubusercontent.com/13063165/220958368-95b03620-3c9b-40a8-be74-01c96ba03cad.png" />

## 使用 Playwright Inspector 生成测试

运行 `codegen` 命令时，会打开两个窗口：一个浏览器窗口，您可以在其中与要测试的网站交互；一个 Playwright Inspector 窗口，您可以在其中录制测试，然后将它们复制到编辑器中。

### 运行 Codegen

使用 `codegen` 命令运行测试生成器，后跟您要为其生成测试的网站的 URL。URL 是可选的，您始终可以在不使用它的情况下运行命令，然后直接在浏览器窗口中添加 URL。

```bash js
npx playwright codegen demo.playwright.dev/todomvc
```

```bash java
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="codegen demo.playwright.dev/todomvc"
```

```bash python
playwright codegen demo.playwright.dev/todomvc
```

```bash csharp
pwsh bin/Debug/netX/playwright.ps1 codegen demo.playwright.dev/todomvc
```

### 录制测试

运行 `codegen` 命令并在浏览器窗口中执行操作。Playwright 将为用户交互生成代码，您可以在 Playwright Inspector 窗口中查看。完成测试录制后，停止录制并按**复制**按钮将生成的测试复制到编辑器中。

使用测试生成器，您可以录制：
* 通过简单地与页面交互来执行点击或填充等操作
* 通过点击工具栏中的图标之一，然后点击页面上的元素进行断言。您可以选择：
  * `'assert visibility'` 断言元素可见
  * `'assert text'` 断言元素包含特定文本
  * `'assert value'` 断言元素具有特定值

######
* langs: js

![录制测试](https://github.com/microsoft/playwright/assets/13063165/34a79ea1-639e-4cb3-8115-bfdc78e3d34d)

######
* langs: java

![录制测试](https://github.com/microsoft/playwright/assets/13063165/ec9c4071-4af8-4ae7-8b36-aebcc29bdbbb)

######
* langs: python

![录制测试](https://github.com/microsoft/playwright/assets/13063165/9751b609-6e4c-486b-a961-f86f177b1d58)

######
* langs: csharp

![录制测试](https://github.com/microsoft/playwright/assets/13063165/53bdfb6f-d462-4ce0-ab95-0619faaebf1e)

######
* langs: js, java, python, csharp

完成与页面的交互后，按**录制**按钮停止录制，并使用**复制**按钮将生成的代码复制到编辑器中。

使用**清除**按钮清除代码以重新开始录制。完成后，关闭 Playwright inspector 窗口或停止终端命令。

### 生成定位器
您可以使用测试生成器生成[定位器](/locators.md)。

* 按"录制"按钮停止录制，然后"选择定位器"按钮将出现。
* 点击"选择定位器"按钮，然后将鼠标悬停在浏览器窗口中的元素上，查看每个元素下方突出显示的定位器。
* 要选择定位器，点击您想要定位的元素，该定位器的代码将出现在"选择定位器"按钮旁边的字段中。
* 然后，您可以在此字段中编辑定位器以进行微调，或使用复制按钮将其复制并粘贴到代码中。

######
* langs: js

![选择定位器](https://github.com/microsoft/playwright/assets/13063165/2c8a12e2-4e98-4fdd-af92-1d73ae696d86)

######
* langs: java

![选择定位器](https://github.com/microsoft/playwright/assets/13063165/733b48fd-5edf-4150-93f0-018adc52b6ff)

######
* langs: python

![选择定位器](https://github.com/microsoft/playwright/assets/13063165/95d11f48-96a4-46b9-9c2a-63c3aa4fdce7)

######
* langs: csharp

![选择定位器](https://github.com/microsoft/playwright/assets/13063165/1478f56f-422f-4276-9696-0674041f11dc)

## 模拟

您可以使用测试生成器通过模拟来生成测试，以便为特定视口、设备、颜色方案生成测试，以及模拟地理位置、语言或时区。测试生成器还可以在保留已认证状态的同时生成测试。

### 模拟视口大小

Playwright 打开的浏览器窗口的视口设置为特定的宽度和高度，且不响应，因为测试需要在相同条件下运行。使用 `--viewport` 选项生成具有不同视口大小的测试。

```bash js
npx playwright codegen --viewport-size="800,600" playwright.dev
```

```bash java
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="codegen --viewport-size='800,600' playwright.dev"
```

```bash python
playwright codegen --viewport-size="800,600" playwright.dev
```

```bash csharp
pwsh bin/Debug/netX/playwright.ps1 codegen --viewport-size="800,600" playwright.dev
```
######
* langs: js

<img width="870" alt="Codegen 为 playwright.dev 网站生成特定视口的测试代码 js" src="https://user-images.githubusercontent.com/13063165/220402029-f90d1c9f-d740-4c0f-acc8-95235ee83f85.png" />

######
* langs: java

<img width="870" alt="Codegen 为 playwright.dev 网站生成特定视口的测试代码 java" src="https://user-images.githubusercontent.com/13063165/220402748-12a856c2-b3ff-4155-b82d-64dad9c46886.png" />

######
* langs: python

<img width="870" alt="Codegen 为 playwright.dev 网站生成特定视口的测试代码 python" src="https://user-images.githubusercontent.com/13063165/220403118-7704b708-dea3-44b3-97a4-04c2b9d1d0fa.png" />

######
* langs: csharp

<img width="870" alt="Codegen 为 playwright.dev 网站生成特定视口的测试代码 dotnet" src="https://user-images.githubusercontent.com/13063165/220403496-4a46a9a1-4bc4-43e7-8f22-9cc760ceadaf.png" />


### 模拟设备

使用 `--device` 选项在模拟移动设备的同时录制脚本和测试，该选项设置视口大小和用户代理等。

```bash js
npx playwright codegen --device="iPhone 13" playwright.dev
```

```bash java
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args='codegen --device="iPhone 13" playwright.dev'
```

```bash python
playwright codegen --device="iPhone 13" playwright.dev
```

```bash csharp
pwsh bin/Debug/netX/playwright.ps1 codegen --device="iPhone 13" playwright.dev
```
######
* langs: js

<img width="1300" alt="Codegen 为 playwright.dev 网站生成 iPhone 13 模拟的测试代码 js" src="https://user-images.githubusercontent.com/13063165/220921482-dc4f5532-9dce-40bd-8a28-e0d87d26a601.png" />

######
* langs: java

<img width="1300" alt="Codegen 为 playwright.dev 网站生成 iPhone 13 模拟的测试代码 java" src="https://user-images.githubusercontent.com/13063165/220922591-241e6a59-a920-4cb1-97a2-d46c33ea17c5.png" />

######
* langs: python

<img width="1300" alt="Codegen 为 playwright.dev 网站生成 iPhone 13 模拟的测试代码 python" src="https://user-images.githubusercontent.com/13063165/220922790-5c5a4d1a-e27d-4c9b-90ac-13cf9c925706.png" />

######
* langs: csharp

<img width="1300" alt="Codegen 为 playwright.dev 网站生成 iPhone 13 模拟的测试代码 csharp" src="https://user-images.githubusercontent.com/13063165/220923048-f13583b1-ab08-4702-ab74-58691d50acfe.png" />


### 模拟颜色方案

使用 `--color-scheme` 选项在模拟颜色方案的同时录制脚本和测试。

```bash js
npx playwright codegen --color-scheme=dark playwright.dev
```

```bash java
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="codegen --color-scheme=dark playwright.dev"
```

```bash python
playwright codegen --color-scheme=dark playwright.dev
```

```bash csharp
pwsh bin/Debug/netX/playwright.ps1 codegen --color-scheme=dark playwright.dev
```

######
* langs: js

<img width="1394" alt="Codegen 为 playwright.dev 网站在暗模式下生成测试代码 js" src="https://user-images.githubusercontent.com/13063165/220930273-f3a25bae-64dd-4bbb-99ed-1e97c0cb1ebf.png" />

######
* langs: java

<img width="1394" alt="Codegen 为 playwright.dev 网站在暗模式下生成测试代码 java" src="https://user-images.githubusercontent.com/13063165/220930514-3b105fab-c87e-4f58-affa-d11d570122a8.png" />

######
* langs: python

<img width="1394" alt="Codegen 为 playwright.dev 网站在暗模式下生成测试代码 python" src="https://user-images.githubusercontent.com/13063165/220930714-737647fd-ae99-4dd3-b7a4-4f3eb4fe712d.png" />

######
* langs: csharp

<img width="1394" alt="Codegen 为 playwright.dev 网站在暗模式下生成测试代码 csharp" src="https://user-images.githubusercontent.com/13063165/220930893-c1d0df65-c662-4b33-91eb-ea10552d7cc5.png" />

### 模拟地理位置、语言和时区

使用 `--timezone`、`--geolocation` 和 `--lang` 选项在模拟时区、语言和位置的同时录制脚本和测试。页面打开后：

1. 接受 cookies
2. 在右上角，点击定位按钮以查看地理位置功能。

```bash js
npx playwright codegen --timezone="Europe/Rome" --geolocation="41.890221,12.492348" --lang="it-IT" bing.com/maps
```

```bash java
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args='codegen --timezone="Europe/Rome" --geolocation="41.890221,12.492348" --lang="it-IT" bing.com/maps'
```

```bash python
playwright codegen --timezone="Europe/Rome" --geolocation="41.890221,12.492348" --lang="it-IT" bing.com/maps
```

```bash csharp
pwsh bin/Debug/netX/playwright.ps1 codegen --timezone="Europe/Rome" --geolocation="41.890221,12.492348" --lang="it-IT" bing.com/maps
```

######
* langs: js

<img width="1394" alt="Codegen 为必应地图生成测试代码，显示时区、地理位置为罗马（意大利）并使用意大利语" src="https://user-images.githubusercontent.com/13063165/220931996-d3144421-8d3b-4f9f-896c-769c01566c01.png" />

######
* langs: java

<img width="1394" alt="Codegen 为必应地图生成测试代码，显示时区、地理位置为罗马（意大利）并使用意大利语 java" src="https://user-images.githubusercontent.com/13063165/220932268-9012163f-7673-4072-aa91-13b3c8f57799.png" />

######
* langs: python

<img width="1394" alt="Codegen 为必应地图生成测试代码，显示时区、地理位置为罗马（意大利）并使用意大利语 python" src="https://user-images.githubusercontent.com/13063165/220932413-f2943956-dd38-4560-94b9-51968076210d.png" />


######
* langs: csharp

<img width="1394" alt="Codegen 为必应地图生成测试代码，显示时区、地理位置为罗马（意大利）并使用意大利语 csharp" src="https://user-images.githubusercontent.com/13063165/220932688-a47df2a8-332b-47a4-9580-7d351def9f50.png" />

### 保存认证状态

使用 `--save-storage` 运行 `codegen` 以在会话结束时保存 [cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)、[localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) 和 [IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API) 数据。这对于单独录制身份验证步骤并在以后录制更多测试时重用它很有用。

```bash js
npx playwright codegen github.com/microsoft/playwright --save-storage=auth.json
```

```bash java
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="codegen github.com/microsoft/playwright  --save-storage=auth.json"
```

```bash python
playwright codegen github.com/microsoft/playwright --save-storage=auth.json
```

```bash csharp
pwsh bin/Debug/netX/playwright.ps1 codegen github.com/microsoft/playwright --save-storage=auth.json
```

######
* langs: js

<img width="1394" alt="登录前的 GitHub 页面 js" src="https://user-images.githubusercontent.com/13063165/220929062-88dfe567-0c6d-4e49-b9f9-74ae241fb8c7.png" />


######
* langs: java

<img width="1394" alt="登录前的 GitHub 页面 java" src="https://user-images.githubusercontent.com/13063165/220929236-08129e16-82a9-46a3-9f1c-3e59619c6289.png" />


######
* langs: python

<img width="1394" alt="登录前的 GitHub 页面 python" src="https://user-images.githubusercontent.com/13063165/220929429-8756ec49-fbf2-46e0-8f41-d25f5f5a6623.png" />

######
* langs: csharp

<img width="1394" alt="登录前的 GitHub 页面 csharp" src="https://user-images.githubusercontent.com/13063165/220929619-28d4ed0c-d172-4cf1-b30b-bf5bed0e07bf.png" />

#### 登录

执行身份验证并关闭浏览器后，`auth.json` 将包含您可以在测试中重用的存储状态。

<img width="1394" alt="登录到 GitHub 屏幕" src="https://user-images.githubusercontent.com/13063165/220561688-04b2b984-4ba6-4446-8b0a-8058876e2a02.png" />

确保您只在本地使用 `auth.json`，因为它包含敏感信息。将其添加到 `.gitignore` 中或在生成测试完成后删除它。

#### 加载认证状态

使用 `--load-storage` 从 `auth.json` 中使用先前加载的存储。这样，所有 [cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)、[localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) 和 [IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API) 数据都将被恢复，使大多数 Web 应用程序无需再次登录即可进入已认证状态。这意味着您可以从已登录状态继续生成测试。

```bash js
npx playwright codegen --load-storage=auth.json github.com/microsoft/playwright
```

```bash java
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="codegen --load-storage=auth.json github.com/microsoft/playwright"
```

```bash python
playwright codegen --load-storage=auth.json github.com/microsoft/playwright
```

```bash csharp
pwsh bin/Debug/netX/playwright.ps1 codegen --load-storage=auth.json github.com/microsoft/playwright
```

######
* langs: js

<img width="1394" alt="显示使用加载存储的已登录 GitHub js" src="https://user-images.githubusercontent.com/13063165/220927873-9e55fdda-2def-45c1-9a1b-bcc851885f96.png" />


######
* langs: java

<img width="1394" alt="显示使用加载存储的已登录 GitHub java" src="https://user-images.githubusercontent.com/13063165/220928075-1e38347b-9d0d-4d9e-9a67-506c717893df.png" />

######
* langs: python

<img width="1394" alt="显示使用加载存储的已登录 GitHub python" src="https://user-images.githubusercontent.com/13063165/220928211-ca1d4dc9-9966-414e-ab23-a3ef1d2d5ed9.png" />

######
* langs: csharp

<img width="1394" alt="显示使用加载存储的已登录 GitHub scharp" src="https://user-images.githubusercontent.com/13063165/220928354-caa0e958-fe09-4125-9b54-67483064da51.png" />

## 使用自定义设置录制

如果您想在某些非标准设置中使用代码生成（例如，使用 [`method: BrowserContext.route`]），可以调用 [`method: Page.pause`]，它将打开一个带有代码生成控件的单独窗口。

```js
const { chromium } = require('@playwright/test');

(async () => {
  // 确保有界面运行。
  const browser = await chromium.launch({ headless: false });

  // 根据需要设置上下文。
  const context = await browser.newContext({ /* 传递任何选项 */ });
  await context.route('**/*', route => route.continue());

  // 暂停页面，然后手动开始录制。
  const page = await context.newPage();
  await page.pause();
})();
```

```java
import com.microsoft.playwright.*;

public class Example {
  public static void main(String[] args) {
    try (Playwright playwright = Playwright.create()) {
      BrowserType chromium = playwright.chromium();
      // 确保有界面运行。
      Browser browser = chromium.launch(new BrowserType.LaunchOptions().setHeadless(false));
      // 根据需要设置上下文。
      BrowserContext context = browser.newContext(/* 传递任何选项 */);
      context.route("**/*", route -> route.resume());
      // 暂停页面，然后手动开始录制。
      Page page = context.newPage();
      page.pause();
    }
  }
}
```

```python async
import asyncio
from playwright.async_api import async_playwright

async def main():
    async with async_playwright() as p:
        # 确保有界面运行。
        browser = await p.chromium.launch(headless=False)

        # 根据需要设置上下文。
        context = await browser.new_context() # Pass any options
        await context.route('**/*', lambda route: route.continue_())

        # 暂停页面，然后手动开始录制。
        page = await context.new_page()
        await page.pause()

asyncio.run(main())
```

```python sync
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    # 确保有界面运行。
    browser = p.chromium.launch(headless=False)

    # 根据需要设置上下文。
    context = browser.new_context() # Pass any options
    context.route('**/*', lambda route: route.continue_())

    # 暂停页面，然后手动开始录制。
    page = context.new_page()
    page.pause()
```

```csharp
using Microsoft.Playwright;

using var playwright = await Playwright.CreateAsync();
var chromium = playwright.Chromium;
// Make sure to run headed.
var browser = await chromium.LaunchAsync(new() { Headless = false });

// Setup context however you like.
var context = await browser.NewContextAsync(); // Pass any options
await context.RouteAsync("**/*", route => route.ContinueAsync());

// Pause the page, and start recording manually.
var page = await context.NewPageAsync();
await page.PauseAsync();
```
