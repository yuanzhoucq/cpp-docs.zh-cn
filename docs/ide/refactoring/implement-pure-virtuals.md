---
title: "实现纯虚 |Microsoft 文档"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f311c2e5832754bfd785084b9aa930b5dbe43845
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="implement-pure-virtuals"></a>实现纯虚方法
**新增功能：**便会立即生成的类中实现所有纯虚方法所需的代码。 

**何时：**你想要从具有纯虚函数的类继承。  

**原因：**但此功能会自动生成所有方法签名，可以手动实现所有纯虚函数一个由一。

**如何：**

1. 文本或鼠标光标置于想要实现的基类纯虚函数的类。

   ![突出显示的代码](images/virtuals_highlight.png)

1. 接下来，请执行以下任一操作：
   * **键盘**
     * 按**Ctrl +。** 向触发器**快速操作和重构**菜单，然后选择**实现所有纯虚拟类的*ClassName** * 从上下文菜单中，其中*类名*是所选类的名称。
   * **鼠标**
     * 右键单击并选择**快速操作和重构**菜单，然后选择**实现所有纯虚拟类的*ClassName** * 从上下文菜单中，其中*类名*是所选类的名称。

1. 纯虚方法签名将自动创建，并且可以实现。

   ![实现纯虚方法结果](images/virtuals_result.png)
