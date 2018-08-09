---
title: 插入 ActiveX 控件对话框 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.insertActiveXControls
dev_langs:
- C++
helpviewer_keywords:
- Insert ActiveX Control dialog box
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: 06638ea3-0726-40da-a989-9b89292d0e3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0201619d463d677eae312d70a543a19887dbdb40
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011785"
---
# <a name="insert-activex-control-dialog-box"></a>“插入 ActiveX 控件”对话框
此对话框可以向[ActiveX 控件插入对话框](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)时使用[对话框编辑器](../windows/dialog-editor.md)。  
  
### <a name="activex-control"></a>ActiveX 控件 
 显示 Active X 控件的列表。 从该对话框中插入控件不会生成一个包装类。 如果您需要一个包装器类，使用[类视图](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925)创建一个 (有关详细信息，请参阅[添加类](../ide/adding-a-class-visual-cpp.md))。 如果 Active X 控件不会出现在此对话框，请尝试安装该控件根据供应商的说明。  
  
### <a name="path"></a>路径  
 显示在其中找到 ActiveX 控件的文件。  
  
 可以放置在控件**工具箱**以方便访问的窗口。 有关详细信息，请参阅[自定义工具箱对话框](http://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [对话框编辑器选项卡工具箱](../windows/dialog-editor-tab-toolbox.md)   
 [资源文件](../windows/resource-files-visual-studio.md)   
 [对话框中的控件](../windows/controls-in-dialog-boxes.md)