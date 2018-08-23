---
title: 将值添加到组合框控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.combo
dev_langs:
- C++
helpviewer_keywords:
- combo boxes [C++], Data property
- controls [Visual Studio], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- controls [C++], testing values in combo boxes
- Data property
- combo boxes [C++], testing values
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c1727313018e88d97f810204428cc99f7aab2366
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591604"
---
# <a name="adding-values-to-a-combo-box-control"></a>向组合框控件添加值

可以将值添加到组合框控件中，只要您具有**对话框**编辑器中，打开。

> [!TIP]
> 它是一个好办法将所有值都添加到组合框*之前*大小的框中**对话框**编辑器中，也可能会截断应在组合框控件中显示的文本。

### <a name="to-enter-values-into-a-combo-box-control"></a>若要在组合框控件中输入值

1. 通过单击选择组合框控件。

2. 在中[属性窗口](/visualstudio/ide/reference/properties-window)，向下滚动到**数据**属性。

   > [!NOTE]
   > 如果您要显示按类型分组的属性**数据**将出现在**杂项**属性。

3. 值区域中单击**数据**属性并键入你的数据值，用分号分隔。

   > [!NOTE]
   > 不要将值之间的空间，因为空格会按字母顺序排列在下拉列表中。

4. 单击**Enter**完后添加值。

扩大的组合框下拉部分的信息，请参阅[设置组合框及其下拉列表的大小](setting-the-size-of-the-combo-box-and-its-drop-down-list.md)。

> [!NOTE]
> 无法将值添加到 Win32 项目使用此过程 (**数据**属性将 Win32 项目灰显)。 因为 Win32 项目没有添加此功能的库，你必须以编程方式添加到 Win32 项目与组合框的值。

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>若要在组合框中测试的值的外观

1. 输入中的值后**数据**属性中，单击**测试**按钮[对话框编辑器工具栏](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)。

   请重试整个值列表中向下滚动。 显示的值中键入与完全**数据**属性中的**属性**窗口。 不不存在任何拼写或大小写检查。

   按**Esc**回到**对话框的**编辑器。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框中的控件](../windows/controls-in-dialog-boxes.md)  
[控件](../mfc/controls-mfc.md)