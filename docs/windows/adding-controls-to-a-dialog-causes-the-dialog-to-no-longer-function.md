---
title: "向对话框添加控件导致对话框不再工作 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0ec4825419c7a9d3c9bc35151b84c327a03325b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>向对话框添加控件导致对话框不再工作
将公共控件或 rich edit 控件添加到对话框中之后, 它时不会显示测试对话框中或对话框本身将不会出现。  
  
 **问题的示例**  
  
1.  创建 Win32 项目中，修改应用程序设置，因此你创建 Windows 应用程序 （不是一个控制台应用程序）。  
  
2.  在[资源视图](../windows/resource-view-window.md)，双击.rc 文件。  
  
3.  在对话框选项中下, 双击**有关**框。  
  
4.  添加**IP 地址控件**到对话框中。  
  
5.  保存和**全部重新生成**。  
  
6.  执行程序。  
  
7.  在对话框中的**帮助**菜单上，单击**有关**命令; 没有对话框显示框。  
  
 **可能的原因**  
  
 目前，对话框编辑器不会自动将代码添加到你的项目时将下列公共控件或 rich edit 控件拖放到对话框。 也不 Visual Studio 提供错误或警告时出现此问题。 您必须手动添加控件的代码。  
  
||||  
|-|-|-|  
|滑块控件|树控件|日期时间选取器|  
|数值调节钮控件|选项卡控件|月历|  
|进度控件|动画控件|IP 地址控件|  
|热键|Rich Edit 控件|扩展的组合框|  
|列表控件|Rich Edit 2.0 控件|自定义控件|  
  
## <a name="the-fix-for-common-controls"></a>公共控件的修复  
 若要使用公共控件出现在对话框中，你需要调用[InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697)或**AFXInitCommonControls**创建对话框之前。  
  
## <a name="the-fix-for-richedit-controls"></a>对 RichEdit 控件的修复  
 必须调用**LoadLibrary**为 rich edit 控件。 有关详细信息，请参阅[RichEdit 1.0 控件使用 MFC](../windows/using-the-richedit-1-0-control-with-mfc.md)，[有关 Rich Edit 控件](http://msdn.microsoft.com/library/windows/desktop/bb787873)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]，和[格式文本编辑控件的概述](../mfc/overview-of-the-rich-edit-control.md)。  
  
## <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [对话框编辑器疑难解答](../windows/troubleshooting-the-dialog-editor.md)   
 [对话框编辑器](../windows/dialog-editor.md)

