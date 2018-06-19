---
title: 对话框控件和代码之间切换 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog editor, accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog editor, switching between controls and code
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ffcb4621bf0005e6b22991da7a2dde9372afa6c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891917"
---
# <a name="switching-between-dialog-box-controls-and-code"></a>在对话框控件和代码之间切换
在 MFC 应用程序，你可以双击对话框控件跳转到其处理程序代码或快速创建存根 （stub） 处理程序函数。  
  
 与选定控件后，单击**控件事件**按钮或**消息**按钮[属性窗口](/visualstudio/ide/reference/properties-window)若要查看 Windows 消息和事件的完整列表可用于所选的项。 从要创建或编辑处理程序函数的列表中选择。  
  
### <a name="to-jump-to-code-from-the-dialog-editor"></a>从对话框编辑器跳转到代码  
  
1.  双击跳转到其最近实现消息处理函数的声明对话框中的控件。 （对于基于 ATL 的对话框类，你始终跳转到构造函数定义。）  
  
### <a name="to-view-events-for-a-control"></a>若要查看控件的事件  
  
1.  与选定控件后，单击**控件事件**按钮[属性窗口](/visualstudio/ide/reference/properties-window)。  
  
    > [!NOTE]
    >  单击**控件事件**按钮时*对话框*在对话框中，你可以展开它以编辑单个控件的事件具有焦点公开所有控件的列表。  
  
     当单个控件具有焦点时在对话框中时，你可以右键单击它并选择**添加事件处理程序**从快捷菜单。 这使你可以指定要向其添加处理程序类。 有关详细信息，请参阅[添加事件处理程序](../ide/adding-an-event-handler-visual-cpp.md)。  
  
### <a name="to-view-messages-for-a-dialog-box"></a>查看对话框中的消息  
  
1.  选择的对话框中，单击**消息**按钮[属性窗口](/visualstudio/ide/reference/properties-window)。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 要求  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [对话框编辑器](../windows/dialog-editor.md)

