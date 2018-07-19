---
title: 显示或隐藏对话框编辑器工具栏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog editor, showing or hiding toolbar
ms.assetid: 93c255e1-90eb-48b6-8602-450acda75bed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ad456d37252b40be72217e6cbc40a2a399bb34ef
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891589"
---
# <a name="showing-or-hiding-the-dialog-editor-toolbar"></a>显示或隐藏对话框编辑器工具栏
打开对话框编辑器时，对话框编辑器工具栏将自动显示在你的解决方案的顶部。  
  
### <a name="dialog-editor-toolbar"></a>对话框编辑器工具栏  
  
|图标|含义|图标|含义|  
|----------|-------------|----------|-------------|  
|![测试对话框按钮](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|“测试”对话框|![空间跨按钮](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|交叉|  
|![对齐左对齐按钮](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|左对齐|![空间向下按钮](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|向下|  
|![对齐权限按钮](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|右对齐|![使宽度相同按钮](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|使宽度相同|  
|![对齐顶部按钮](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|顶部对齐|![使高度相同按钮](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|使高度相同|  
|![对齐底部按钮](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|底部对齐|![使大小相同按钮](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|使大小相同|  
|![Center 垂直按钮](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertical")|垂直|![切换网格按钮](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|切换网格|  
|![水平居中按钮](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|水平|![切换参考线按钮](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|切换参考线|  
  
 对话框编辑器工具栏包含用于排列控件在对话框中，例如大小和对齐方式的布局的按钮。 对话框编辑器工具栏按钮对应于格式菜单上的命令。 有关详细信息，请参阅[对话框编辑器的快捷键](../windows/accelerator-keys-for-the-dialog-editor.md)。  
  
 当你在对话框编辑器时，你可以通过从可用工具栏和窗口的列表中选择切换显示的对话框编辑器工具栏。  
  
### <a name="to-show-or-hide-the-dialog-editor-toolbar"></a>若要显示或隐藏对话框编辑器工具栏  
  
1.  上**视图**菜单上，单击**工具栏**然后选择**对话框编辑器**从子菜单。  
  
    > [!NOTE]
    >  当对话框编辑器; 中打开对话框资源时，默认显示的对话框编辑器工具栏但是，如果你显式关闭工具栏，你将需要打开对话框资源下一次调用它。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 要求  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [对话框上的控件排列](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [如何： 创建资源](../windows/how-to-create-a-resource.md)   
 [资源文件](../windows/resource-files-visual-studio.md)   
 [对话框编辑器](../windows/dialog-editor.md)

