---
title: "Adding Controls to a Dialog Causes the Dialog to No Longer Function | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "controls [C++], troubleshooting"
  - "common controls, troubleshooting"
  - "troubleshooting controls"
  - "dialog boxes, troubleshooting"
  - "dialog box controls, troubleshooting"
  - "InitCommonControls"
ms.assetid: b2dd4574-ea59-4343-8d65-b387cead5da6
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Controls to a Dialog Causes the Dialog to No Longer Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将公共控件或 Rich Edit 控件添加到对话框之后，在测试对话框时该控件不出现，或者对话框本身不出现。  
  
 **问题示例**  
  
1.  创建 Win32 项目，修改应用程序设置以创建 Windows 应用程序（不是控制台应用程序）。  
  
2.  在[资源视图](../windows/resource-view-window.md)中，双击 .rc 文件。  
  
3.  在对话框选项下，双击**“关于”**框。  
  
4.  将一个“IP Address Control”添加到对话框。  
  
5.  保存并“重新生成”。  
  
6.  执行程序。  
  
7.  在对话框的**“帮助”**菜单上，单击**“关于”**命令；没有显示任何对话框。  
  
 **原因**  
  
 目前，将下列公共控件或 Rich Edit 控件拖放到对话框上时，对话框编辑器不自动在项目中添加代码。  当此问题发生时，Visual Studio 既不提供错误也不进行警告。  必须手动为控件添加代码。  
  
||||  
|-|-|-|  
|滑块控件|树控件|日期时间选取器|  
|数值调节钮控件 \(Spin Control\)|选项卡控件|月历|  
|进度控件|动画控件 \(Animation Control\)|IP 地址控件 \(IP Address Control\)|  
|热键 \(Hot Key\)|Rich Edit 控件 （Rich Edit Control）|扩展组合框 \(Extended Combo Box\)|  
|列表控件|Rich Edit 2.0 控件 \(Rich Edit 2.0 Control\)|自定义控件|  
  
## 公共控件的修复  
 为了在对话框上使用公共控件，需要在创建对话框之前调用 [InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697) 或 **AFXInitCommonControls**。  
  
## RichEdit 控件的修复  
 必须为 Rich Edit 控件调用 **LoadLibrary**。  有关更多信息，请参见 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的[对 RichEdit 1.0 控件使用 MFC](../mfc/using-the-richedit-1-0-control-with-mfc.md)、[关于 Rich Edit 控件](http://msdn.microsoft.com/library/windows/desktop/bb787873)，以及 [Rich Edit 控件概述](../mfc/overview-of-the-rich-edit-control.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Troubleshooting the Dialog Editor](../mfc/troubleshooting-the-dialog-editor.md)   
 [Dialog Editor](../mfc/dialog-editor.md)