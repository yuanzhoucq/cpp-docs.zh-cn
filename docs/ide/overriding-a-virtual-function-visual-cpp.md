---
title: 替代虚函数
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.virtualfunc.override
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
ms.openlocfilehash: 9bb3fd34bbfa14cce1595ed586c4e1b66518e7b7
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694018"
---
# <a name="override-a-virtual-function"></a>替代虚函数

可以从 Visual Studio [属性窗口](/visualstudio/ide/reference/properties-window)替代基类中定义的虚函数。

**在属性窗口中替代虚函数：**

1. 在“类视图”中，选择类。

1. 在“属性”窗口中，选择“替代”按钮。

   > [!NOTE]
   > 在“类视图”中选择类名或在源窗口中选择时，“替代”按钮才会显示。

   左列列出了虚函数。 如果虚函数的名称还在右列中显示，则已实现替代。

1. 如果函数没有替代，则选择属性窗口右列中的单元格会将函数替代的建议名称显示为 \<add>FuncName。

1. 选择建议名称，为函数添加存根代码。

1. 若要编辑替代函数，请在类视图中双击函数名并在源窗口中编辑代码。

要删除替代，请在右列中选择替代函数名并选择 \<delete>FuncName。 即注释掉函数的代码。
