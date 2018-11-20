---
title: 实现纯虚方法
ms.date: 11/16/2016
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
ms.openlocfilehash: 59e4519f57a1d9bd9ba1cee1ed6ae41bea785a9f
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692655"
---
# <a name="implement-pure-virtuals"></a>实现纯虚方法

功能：让你可以立即生成实现类中所有纯虚方法所需的代码。

时间：想要从具有纯虚函数的类中继承时使用该功能。

原因：可以手动逐一实现所有纯虚函数，但此功能可自动生成所有方法签名。

方法：

1. 将文本或鼠标光标置于想要在其中实现基类的纯虚函数的类上。

   ![突出显示的代码](images/virtuals_highlight.png)

1. 接下来，执行以下操作之一：
   * **键盘**
     * 按“Ctrl+.” 触发“快捷操作和重构”菜单并从上下文菜单选择“实现 "ClassName" 类的所有纯虚方法”，其中 ClassName 是所选类的名称。
   * **鼠标**
     * 右键单击并选择“快捷操作和重构”菜单并从上下文菜单选择“实现 "ClassName" 类的所有纯虚方法”，其中 ClassName 是所选类的名称。

1. 将自动创建纯虚方法签名，以供实现。

   ![实现纯虚方法结果](images/virtuals_result.png)
