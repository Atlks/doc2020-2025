
Node dsktp app  electron prblm


TypeError: Cannot read properties of undefined (reading 'whenReady')
Should use elecron .exe boot.not  node



Electron的 webview 标签基于 Chromium webview ，后者正在经历巨大的架构变化。 这将影响 webview 的稳定性，包括呈现、导航和事件路由。 我们目前建议不使用 webview 标签，并考虑其他替代方案，如 iframe ，Electron的 BrowserView 或完全避免嵌入内容的架构。
