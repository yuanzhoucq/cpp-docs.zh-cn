---
title: 移动定义位置 | Microsoft Docs
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
ms.openlocfilehash: 5058e0b3bab1fb5fb5e8d52b55e3fa7c37fd8a4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430032"
---
# <a name="move-definition-location"></a>移动定义位置
功能：让你可以将函数定义立即移动到相应的头文件。

时间：具有一个想要移动到头文件的函数时使用该功能。

原因：可以手动移动该函数，但此功能将自动移动函数，在必要时创建头文件。

方法：

1. 将文本或鼠标光标置于要移动的函数上。

   ![突出显示的代码](images/movedefinition_highlight.png)

1. 接下来，执行以下操作之一：
   * **键盘**
     * 按“Ctrl+.” 触发“快速操作和重构”菜单，然后从快捷菜单选择“移动定义位置”。
   * **鼠标**
     * 右键单击并选择“快速操作和重构”菜单，然后从快捷菜单选择“移动定义位置”。

1. 此函数随即被移动到相应的头文件中，你将在弹出预览窗口看到此内容。  如果头文件不存在，也将创建它并将其放置在项目中。

   ![“创建声明/定义”结果](images/movedefinition_result.png)
