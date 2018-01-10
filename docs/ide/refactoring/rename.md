---
title: "重命名 |Microsoft 文档"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64b42a88-3bd9-4399-8b96-75bceffc353b
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7ca06ef5a11d674d35aff7276e14312c456c60e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="rename"></a>重命名
**新增功能：**允许你重命名代码符号，如字段、 局部变量、 方法、 命名空间、 属性和类型的标识符。

**何时：**你想要安全地将内容无需查找所有实例，并复制/粘贴新名称重命名。  

**原因：**中复制和粘贴在整个项目的新名称很可能会导致错误。  此重构工具将准确地执行重命名操作。

**如何：**

1. 突出显示，或将文本光标置于要重命名的项：

   ![突出显示的代码](images/rename_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl + R**，然后**Ctrl + R**。  （请注意，键盘快捷方式可能因所选的配置文件而有所不同。）
   * **鼠标**
     * 选择**编辑 > 重构 > 重命名**。
     * 右键单击该代码，然后选择**重命名**。

1. 在**重命名**窗口弹出，输入新名称的所选的项目，然后单击**预览**按钮。  更改**搜索作用域**如果需要扩大或缩小重命名的范围。

   ![重命名对话框](images/rename_dialog.png)

   > [!TIP]
   > 可以通过检查跳过预览**跳过预览更改如果所有确认引用**选项。

1. 当**预览更改-重命名**窗口随即出现，请确保相应地进行您请求的更改。  使用在窗口的上半复选框启用或禁用任何项重命名。

   ![重命名预览](images/rename_preview.png)

1. 当一切看上去正常时，则单击**应用**按钮和的项将被重命名你的源代码中。
