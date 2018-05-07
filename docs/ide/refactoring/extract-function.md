---
title: 提取函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fc4d48c972bca9352f326085574e4cf4df83aea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="extract-function"></a>提取函数
**新增功能：**允许你的代码片段将转换为其自己的函数。

**何时：**某些需要从另一个函数调用的函数中具有的现有代码片段。  

原因：可以复制/粘贴该代码，但这样会导致重复。  更好的解决方案是该片段重构到其自己的函数可以随意调用的任何其他函数。

方法：

1. 突出显示要提取的代码：

   ![突出显示的代码](images/extractfunction_highlight.png)

1. 接下来，执行以下操作之一：
   * **键盘**
     * 按“Ctrl+R”，然后按“Ctrl+M”。  （请注意，键盘快捷方式可能因所选的配置文件而有所不同。）
     * 按“Ctrl+.” 向触发器**快速操作和重构**菜单，然后选择**提取函数 （实验）**从上下文菜单。
   * **鼠标**
     * 选择**编辑 > 重构 > 提取函数 （实验）**。
     * 右键单击代码中，选择**快速操作和重构**菜单，然后选择**提取函数 （实验）**从上下文菜单。
     * 单击![Lightbulb](images/bulb.png)图标显示在左边的距和选择**提取函数 （实验）**从上下文菜单。

1. 在**提取函数/方法 （实验）**窗口中，输入新的函数名称，选择需要代码的位置放置，并单击**确定**按钮。  

   ![提取函数函数](images/extractfunction_dialog.png)

1. 将创建新的函数在指定的函数原型中的相应的头文件，并将更改的原始代码以调用该函数。

   ![提取函数结果](images/extractfunction_result.png)