---
title: "使用 OLE/COM 对象查看器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件 [C++], 查看内部接口"
  - "自动化对象的对象查看器"
  - "OLE/COM 对象查看器"
ms.assetid: a3359e31-2869-451d-9571-129b4e8b41f0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 使用 OLE/COM 对象查看器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以使用 OLE\/COM 对象查看器查看控件的接口。  
  
### 使用 OLE\/COM 对象查看器  
  
1.  启动 OLE\/COM 对象查看 \(oleview.exe\)，在\\Program Files \(x86\)\\Windows Kits \\ 8.0 \\ bin \\ x86 \\文件夹中。  
  
2.  在查看器的**Object Classes, Grouped by Component** 目录在，打开 **Automation Objects** 文件夹来查看已经注册的自动化对象。  
  
3.  请选择其他控件之一。  右窗格中会出现几个选项卡，由该控件实现的接口显示在“注册表”选项卡中。  
  
    -   如果打开左窗格中的控件并选择“查看类型信息”快捷菜单，ITypeInfo 查看器将显示重建后的 .idl 或 .odl 文件。  
  
    -   如果展开左窗格中的控件节点，将看到对象中的接口列表。  如果选择，接口的注册表项将显示在右窗格中。  
  
    -   如果打开某接口的快捷菜单并选择**“查看”**，OLE\/COM 对象查看器将显示一个对话框来显示该接口的 GUID，和一个用于查看类型库信息（如果该信息可用）的选项。  选择“查看类型信息”将在 ITypeInfo 查看器中显示特定于该接口的重建 .idl 文件的一部分。  
  
    -   在 ITypeInfo 查看器中，选择树视图中的接口成员来显示右窗格中显示访问器方法签名。  
  
## 请参阅  
 [使用 ActiveX 控件](../../data/ado-rdo/using-activex-controls.md)