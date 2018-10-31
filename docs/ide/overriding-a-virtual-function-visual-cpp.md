---
title: 替代虚函数 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.virtualfunc.override
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c150360294277653c777e5142cbf1dc57a97b2b2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409780"
---
# <a name="overriding-a-virtual-function-visual-c"></a>重写虚函数 (Visual C++)

可以从 Visual Studio [属性窗口](/visualstudio/ide/reference/properties-window)替代基类中定义的虚函数。

### <a name="to-override-a-virtual-function-in-the-properties-window"></a>在属性窗口中替代虚函数

1. 在“类视图”中，单击此类。

1. 在“属性”窗口中，单击“替代”按钮。

   > [!NOTE]
   >  在“类视图”中选择类名或在源窗口中单击时，“替代”按钮才会显示。

   左列列出了虚函数。 如果虚函数的名称还在右列中显示，则已实现替代。

1. 如果函数没有替代，则单击属性窗口右列中的单元格会将函数替代的建议名称显示为 \<add>FuncName。

1. 单击建议名称，为函数添加存根代码。

1. 若要编辑替代函数，请在类视图中双击函数名并在源窗口中编辑代码。

若要删除替代，请在右列中单击替代函数名并选择 \<delete>FuncName。 即注释掉函数的代码。

## <a name="see-also"></a>请参阅

[用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[添加类](../ide/adding-a-class-visual-cpp.md)<br>
[添加成员函数](../ide/adding-a-member-function-visual-cpp.md)<br>
[添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)<br>
[MFC 消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[导航类结构](../ide/navigating-the-class-structure-visual-cpp.md)