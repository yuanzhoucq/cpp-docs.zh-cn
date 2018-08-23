---
title: 如何： 在资源中的搜索符号 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols, finding
- resources [Visual Studio], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3aada3dac208fcf08a9b0e61ef822c3ab13b7b44
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605761"
---
# <a name="how-to-search-for-symbols-in-resources"></a>如何：在资源中搜索符号

### <a name="to-find-symbols-in-resources"></a>在资源中查找符号

1. 从**编辑**菜单中，选择**查找符号**。

2. 在中[查找符号对话框](http://msdn.microsoft.com/63e93d9c-784f-418d-a76a-723da5ff5d96)，在**查找内容**框中，从下拉列表中选择以前的搜索字符串或键入想要查找 （例如 ID_ACCEL1） 的加速键。

   > [!TIP]
   > 若要使用[正则表达式](/visualstudio/ide/using-regular-expressions-in-visual-studio)为你的搜索，必须使用[在文件中查找](/visualstudio/ide/reference/find-command)从**编辑**而不是菜单**查找符号**命令。 若要启用正则表达式，必须具有**使用： 正则表达式**中所选的复选框[查找对话框](http://msdn.microsoft.com/dad03582-4931-4893-83ba-84b37f5b1600)。 然后，您可以单击右侧的向右箭头按钮**查找内容**框，以显示搜索正则表达式的列表。 当从此列表中选择一个表达式时，它将替换中的搜索文本**查找内容**框。

3. 选择任一**查找**选项。

4. 单击**查找下一个**。

   > [!NOTE]
   > 无法搜索字符串、快捷键或二进制资源中的符号。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息以及 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[符号：资源标识符](../windows/symbols-resource-identifiers.md)  
[资源文件](../windows/resource-files-visual-studio.md)  
[资源编辑器](../windows/resource-editors.md)