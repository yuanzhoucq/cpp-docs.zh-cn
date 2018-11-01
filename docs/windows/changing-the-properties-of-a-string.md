---
title: 更改属性的字符串资源 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- resource identifiers, string properties
- string tables [C++], changing strings
- strings [C++], properties
ms.assetid: 0a220434-f444-4405-9a64-d28d6b965687
ms.openlocfilehash: efa5f690b18c223c60a68071b335a881633845d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450981"
---
# <a name="changing-the-properties-of-a-string-resource-c"></a>更改属性的字符串资源 （c + +）

### <a name="to-change-a-string-or-its-identifier"></a>若要更改字符串或其标识符

1. 通过双击中对应的图标打开字符串表[资源视图](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 选择你想要编辑，然后双击的字符串**ID**，**值**，或**标题**列。 现在，你可以：

   - 选择**ID**从**ID 下拉列表**列表中或类型`ID`直接在位置中。

   - 键入在不同的数字**值**列。

   - 键入中的编辑**标题**列。

        > [!NOTE]
        >  此外可以编辑字符串的属性中[属性窗口](/visualstudio/ide/reference/properties-window)。

有关将资源添加到托管项目 （项目面向公共语言运行时） 的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[演练： 本地化 Windows 窗体](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[字符串编辑器](../windows/string-editor.md)