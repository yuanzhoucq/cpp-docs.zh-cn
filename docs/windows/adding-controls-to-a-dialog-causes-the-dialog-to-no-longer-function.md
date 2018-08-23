---
title: 向对话框添加控件导致对话框不再工作 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], troubleshooting
- common controls, troubleshooting
- troubleshooting controls
- dialog boxes, troubleshooting
- dialog box controls, troubleshooting
- InitCommonControls
ms.assetid: b2dd4574-ea59-4343-8d65-b387cead5da6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c1cb1a1894f3288e2825c5eb7d521a468ccdfa7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592809"
---
# <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>向对话框添加控件导致对话框不再工作

将公共控件或 rich edit 控件添加到对话框中之后, 它不会出现时测试对话框的或对话框中本身将不会出现。

### <a name="example-of-the-problem"></a>问题示例

1. 创建 Win32 项目，修改应用程序设置，因此创建 Windows 应用程序 （不是一个控制台应用程序）。

2. 在中[资源视图](../windows/resource-view-window.md)，双击.rc 文件。

3. 在对话框中选项下, 双击**有关**框。

4. 添加**IP 地址控件**到对话框。

5. 保存并**全部重新生成**。

6. 执行该程序。

7. 在对话框中**帮助**菜单上，单击**有关**命令; 没有对话框框中显示。

### <a name="the-cause"></a>原因

目前，对话框编辑器不会不会自动将代码添加到你的项目时以下常用控件或 rich edit 控件拖放到对话框。 也不会 Visual Studio 提供的错误或警告时出现此问题。 必须手动添加控件的代码。

||||
|-|-|-|
|滑块控件|树控件|日期时间选取器|
|数值调节钮控件|选项卡控件|月历|
|进度控件|动画控件|IP 地址控件|
|热键|Rich Edit 控件|扩展的组合框|
|列表控件|Rich Edit 2.0 控件|自定义控件|

## <a name="the-fix-for-common-controls"></a>公共控件的修复

若要使用公共控件出现在对话框中，您需要调用[InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697)或`AFXInitCommonControls`创建对话框的之前。

## <a name="the-fix-for-richedit-controls"></a>对 RichEdit 控件的修复

必须调用`LoadLibrary`rich edit 控件。 有关详细信息，请参阅[RichEdit 1.0 控件使用 MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)，[有关 Rich Edit 控件](http://msdn.microsoft.com/library/windows/desktop/bb787873)在 Windows SDK 中，并[格式文本编辑控件的概述](../mfc/overview-of-the-rich-edit-control.md)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框编辑器疑难解答](../windows/troubleshooting-the-dialog-editor.md)  
[对话框编辑器](../windows/dialog-editor.md)