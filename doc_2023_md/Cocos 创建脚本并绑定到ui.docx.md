Cocos 创建脚本并绑定到ui



创建第一个脚本

通常游戏都是由不同的脚本驱动的，Cocos Creator 使用的是名为 TypeScript 的语言，它是由微软开发，拥有简单易学的语法，强大的类型检测以及广泛的应用。 您可以在网页开发、应用开发以及游戏开发中遇到它的身影。

在 Cocos Creator 中创建脚本是非常简单的，您只需要在 资源管理器 窗口上点击右键，选择 创建 并点击 脚本 项即可。

通常我们会选择创建一个新的目录来存放这些脚本，接下来我们将创建一个名为 'Scripts' 的目录并新建一个名为 PlayerController 的脚本用于控制角色：

create-scripts.gif

这样由引擎模板创建的脚本为组件，他的代码如下：

import { _decorator, Component, Node } from 'cc';
const { ccclass, property } = _decorator;

@ccclass('PlayerController')
export class PlayerController extends Component {
    start() {

    }

    update(deltaTime: number) {

    }
}

组件 必须要挂在在某个节点上才会生效，因此尝试将 PlayerController 脚本拖拽到 Player 节点的 属性检查器上：
