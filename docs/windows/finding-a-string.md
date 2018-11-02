---
title: 查找字符串资源 （c + +） |Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- vc.editors.string
helpviewer_keywords:
- strings [C++], searching
- strings [C++]
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
ms.openlocfilehash: 0e6d8ac8027028377e903a9e0a3c89238a9862a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585911"
---
# <a name="finding-a-string-resource-c"></a>查找字符串资源 （c + +）

可以搜索在字符串表中的一个或多个字符串并使用[正则表达式](/visualstudio/ide/using-regular-expressions-in-visual-studio)与**在文件中查找**命令 (**编辑**菜单) 查找字符串的所有实例模式相匹配。

### <a name="to-find-a-string-in-the-string-table"></a>若要在字符串表中查找字符串

1. 通过双击中对应的图标打开字符串表[资源视图](../windows/resource-view-window.md)。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 上**编辑**菜单上，单击**查找和替换**，然后选择**查找**。

3. 在中**查找内容**框中，从下拉列表中选择以前的搜索字符串或键入想要查找的字符串的标题文本或资源标识符。

4. 选择任一**查找**选项。

5. 单击**查找下一个**。

   > [!TIP]
   > 若要使用的正则表达式搜索文件时，使用**在文件中查找**命令。 键入要与模式匹配，或单击右侧的按钮的正则表达式**查找内容**框，以显示搜索正则表达式的列表。 当从此列表中选择一个表达式时，它将替换中的搜索文本**查找内容**框。 如果使用正则表达式，请确保**使用： 正则表达式**复选框处于选中状态。

有关将资源添加到托管项目 （项目面向公共语言运行时） 的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[演练： 本地化 Windows 窗体](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[字符串编辑器](../windows/string-editor.md)