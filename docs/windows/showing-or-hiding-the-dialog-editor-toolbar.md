---
title: 显示或隐藏对话框编辑器工具栏 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog Editor [C++], showing or hiding toolbar
ms.assetid: 93c255e1-90eb-48b6-8602-450acda75bed
ms.openlocfilehash: e025f560a47f85d17b8c56a4db19f322069d33ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631083"
---
# <a name="showing-or-hiding-the-dialog-editor-toolbar-c"></a>显示或隐藏对话框编辑器工具栏 （c + +）

当打开**对话框中**在 c + + 项目中，编辑器**对话框编辑器**工具栏将自动显示在你的解决方案的顶部。

### <a name="dialog-editor-toolbar"></a>对话框编辑器工具栏

|图标|含义|图标|含义|
|----------|-------------|----------|-------------|
|![测试对话框按钮](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|“测试”对话框|![横向间隔按钮](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|交叉|
|![对齐左对齐按钮](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|左对齐|![纵向间隔按钮](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|向下|
|![对齐权限按钮](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|右对齐|![使宽度相同按钮](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|使宽度相同|
|![您顶部的按钮对齐](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|顶部对齐|![使高度相同按钮](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|使高度相同|
|![对齐底部按钮](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|底部对齐|![使大小相同按钮](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|使大小相同|
|![垂直居中按钮](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|垂直|![切换网格按钮](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|切换网格|
|![水平居中按钮](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|水平|![切换参考线按钮](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|切换参考线|

**对话框编辑器**工具栏包含用于安排上的对话框中，例如大小和对齐方式的控件布局的按钮。 **对话框编辑器**上的工具栏按钮对应于命令**格式**菜单。 有关详细信息，请参阅[对话框编辑器的快捷键](../windows/accelerator-keys-for-the-dialog-editor.md)。

当你处于**对话框中**编辑器中，您可以切换显示**对话框编辑器**可用工具栏和窗口的列表中选择的工具栏。

### <a name="to-show-or-hide-the-dialog-editor-toolbar"></a>若要显示或隐藏对话框编辑器工具栏

1. 上**视图**菜单上，单击**工具栏**然后选择**对话框编辑器**子菜单中。

   > [!NOTE]
   > **对话框编辑器**在对话框编辑器中打开对话框资源时，默认情况下显示的工具栏; 但是，如果您显式关闭工具栏，您将需要调用它在下一次打开对话框资源。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[对话框上的控件排列](../windows/arrangement-of-controls-on-dialog-boxes.md)<br/>
[如何：创建资源](../windows/how-to-create-a-resource.md)<br/>
[资源文件](../windows/resource-files-visual-studio.md)<br/>
[对话框编辑器](../windows/dialog-editor.md)