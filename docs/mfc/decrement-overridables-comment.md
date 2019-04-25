---
title: --Overridables 注释
ms.date: 11/04/2016
helpviewer_keywords:
- Overridables comment in MFC source files
- MFC source files, Overridables comment
- overriding, Overridables comment in MFC source files
- comments, MFC
ms.assetid: 8968dea5-0d94-451f-bcb2-991580e65ba2
ms.openlocfilehash: 90d6a585f62de589299147edce87332d96c6dbb8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153225"
---
# <a name="-overridables-comment"></a>// Overridables 注释

MFC 类声明的 `// Overridables` 部分包含您在需要修改基类行为时可在派生类中重写的虚拟函数。 它们的名称通常以“On”开头，但不是绝对必需的。 此处的函数设计为进行重写，并且一般实现或提供某种“回调”或“挂钩”。 通常，这些成员是受保护的。

在 MFC 本身中，纯虚拟函数始终放置在此节中。 C++ 中的纯虚拟函数使用下列形式之一：

`virtual void OnDraw( ) = 0;`

在类中列出的示例`CStdioFile`，请在[注释示例](../mfc/an-example-of-the-comments.md)，该列表包含没有可重写部分。 类`CDocument`，另一方面，列出了大约 10 个可重写成员函数。

在部分类中，您还可以查看注释 `// Advanced Overridables`。 这些是仅高级程序员应尝试重写的函数。 您可能从不需要重写它们。

> [!NOTE]
>  一般而言，本文中描述的约定也适用于自动化（之前称为“OLE 自动化”）方法和属性。 自动化方法类似于 MFC 操作。 自动化属性类似于 MFC 特性。 自动化事件（受 ActiveX 控件（之前称为“OLE 控件”）支持）类似于 MFC 可重写成员函数。

## <a name="see-also"></a>请参阅

[使用 MFC 源文件](../mfc/using-the-mfc-source-files.md)<br/>
[注释示例](../mfc/an-example-of-the-comments.md)<br/>
[Implementation 注释](../mfc/decrement-implementation-comment.md)<br/>
[构造函数注释](../mfc/decrement-constructors-comment.md)<br/>
[Attributes 注释](../mfc/decrement-attributes-comment.md)<br/>
[Operations 注释](../mfc/decrement-operations-comment.md)
