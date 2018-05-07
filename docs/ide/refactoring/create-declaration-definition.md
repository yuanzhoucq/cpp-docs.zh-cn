---
title: 创建声明 / 定义 |Microsoft 文档
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60d583ec47a3f9c5b61599a5945e3cfa0d375b1d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="create-declaration--definition"></a>创建声明/定义
**新增功能：**便会立即生成的声明或定义的函数。

**何时：**你具有需要 delcaration 或进行相反的转换函数。  

**原因：**你可以手动创建声明/定义，但这将创建它自动，必要时创建的标头/代码文件。

方法：

1. 文本或鼠标光标置于想要创建的声明或定义的函数。

   ![突出显示的代码](images/createdefinition_highlight.png)

1. 接下来，执行以下操作之一：
   * **键盘**
     * 按“Ctrl+.” 向触发器**快速操作和重构**菜单，然后选择**创建声明 / 定义**从上下文菜单。
   * **鼠标**
     * 右键单击并选择**快速操作和重构**菜单，然后选择**创建声明 / 定义**从上下文菜单。

1. 将在源文件或头文件，你将看到在弹出窗口的预览窗口中创建函数的声明/定义。  如果源文件或头文件不存在，将还会创建并放在项目中。

   ![创建声明 / 定义导致](images/createdefinition_result.png)
