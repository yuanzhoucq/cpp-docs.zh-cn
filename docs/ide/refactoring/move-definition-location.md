---
title: 移动定义位置 |Microsoft 文档
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44211105429e33c136999a7877ac6ee42af29f17
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="move-definition-location"></a>移动定义位置
**新增功能：**允许您立即将函数定义移到相应的标头文件。

**何时：**具有你想要将移到标头文件的函数。  

**原因：**你无法手动移动函数，但此功能将会移动它自动，必要时创建的标头文件。

方法：

1. 文本或鼠标光标置于想要移动的函数。

   ![突出显示的代码](images/movedefinition_highlight.png)

1. 接下来，执行以下操作之一：
   * **键盘**
     * 按“Ctrl+.” 向触发器**快速操作和重构**菜单，然后选择**移动定义位置**从上下文菜单。
   * **鼠标**
     * 右键单击并选择**快速操作和重构**菜单，然后选择**移动定义位置**从上下文菜单。

1. 该函数将被移动到相应的头文件，你将看到在弹出窗口的预览窗口中。  如果标头文件不存在，将还会创建并放在项目中。

   ![创建声明 / 定义导致](images/movedefinition_result.png)
