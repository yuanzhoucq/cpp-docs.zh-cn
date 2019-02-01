---
title: 故障排除对话框编辑器中 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 21882868-5ac4-4a41-a4a6-eaaa059402ea
ms.openlocfilehash: fe0fe704b5c17d0db4e3419f29d21f0e60bc4211
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484950"
---
# <a name="troubleshooting-the-dialog-editor-c"></a>故障排除对话框编辑器中 （c + +）

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

以下是几个问题，其中你应在 c + + 中工作时注意**对话框**编辑器：

## <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>向对话框添加控件导致对话框不再工作

将公共控件或 rich edit 控件添加到对话框中之后, 它不会出现时测试对话框的或对话框中本身不会显示。

### <a name="example-of-the-problem"></a>问题示例

1. 创建 Win32 项目，修改应用程序设置，因此创建 Windows 应用程序 （不是一个控制台应用程序）。

1. 在中[资源视图](../windows/resource-view-window.md)，双击.rc 文件。

1. 在下，对话框选项中，双击**有关**框。

1. 添加**IP 地址控件**到对话框。

1. 保存并**全部重新生成**。

1. 执行该程序。

1. 在对话框中**帮助**菜单上，单击**有关**命令; 没有对话框框中显示。

### <a name="the-cause"></a>原因

目前，**对话框**编辑器不会自动将代码添加到你的项目时将下列公共控件或 rich edit 控件拖放到对话框。 也不会 Visual Studio 提供的错误或警告时出现此问题。 若要修复，请手动添加控件的代码。

||||
|-|-|-|
|滑块控件|树控件|日期时间选取器|
|数值调节钮控件|选项卡控件|月历|
|进度控件|动画控件|IP 地址控件|
|热键|Rich Edit 控件|扩展的组合框|
|列表控件|Rich Edit 2.0 控件|自定义控件|

### <a name="fix-for-common-controls"></a>修复了公共控件

若要使用公共控件出现在对话框中，您需要调用[InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex)或`AFXInitCommonControls`创建对话框的之前。

### <a name="fix-for-richedit-controls"></a>对 RichEdit 控件进行了修复

必须调用`LoadLibrary`rich edit 控件。 有关详细信息，请参阅[有关 Rich Edit 控件](/windows/desktop/Controls/about-rich-edit-controls)Windows SDK 中并[的格式文本编辑控件概述](../mfc/overview-of-the-rich-edit-control.md)。

### <a name="requirements"></a>要求

Win32

## <a name="using-the-richedit-10-control-with-mfc"></a>对 RichEdit 1.0 控件使用 MFC

若要使用 RichEdit 控件，必须首先调用[AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2)加载 RichEdit 2.0 控件 (RICHED20。DLL)，或调用[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)加载较旧的 RichEdit 1.0 控件 (RICHED32。DLL)。

可以使用当前[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)类与较旧的 RichEdit 1.0 控件，但`CRichEditCtrl`不仅旨在支持 RichEdit 2.0 控件。 RichEdit 1.0 和 RichEdit 2.0 很相似，因为大多数方法起作用。 但请注意有一些差异的 1.0 和 2.0 的控件，因此，某些方法可能工作不正常或根本不起作用。

### <a name="requirements"></a>要求

MFC

## <a name="see-also"></a>请参阅

[对话框编辑器](../windows/dialog-editor.md)