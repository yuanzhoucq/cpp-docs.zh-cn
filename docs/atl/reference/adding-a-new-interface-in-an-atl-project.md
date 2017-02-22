---
title: "在 ATL 项目中添加新接口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.interface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目, 添加接口"
  - "控件 [ATL], 接口"
  - "实现接口 ATL 向导"
  - "接口, 添加到 ATL 对象"
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 在 ATL 项目中添加新接口
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当向对象或者控件添加接口时，为该接口中的每个方法创建无存根 \(stubbed\-out\) 函数。  在对象或者控件中，可以添加当前仅在现有类型库中找到的接口。  另外，添加接口的类必须实现 [BEGIN\_COM\_MAP](../Topic/BEGIN_COM_MAP.md) 宏，如果项目被特性化，则它必须有 `coclass` 特性。  
  
 可以用两种方法之一向控件中添加新接口：手动或者在类视图中使用代码向导。  
  
### 在类视图中使用代码向导向现有的对象或者控件添加接口  
  
1.  在[“类视图”](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，右击控件的类名。  例如完整控件或者复合控件，或者任何其他在头文件中实现 BEGIN\_COM\_MAP 宏的控件类。  
  
2.  在快捷菜单上单击“添加”，再单击**“实现接口”**。  
  
3.  选择要在[实现接口向导](../../ide/implement-interface-wizard.md)中实现的接口。  如果接口在任何可用的类型库中都不存在，则必须手动将它加到 .idl 文件。  
  
### 手动添加新接口  
  
1.  向 .idl 文件添加新接口的定义。  
  
2.  从接口导出对象或者控件。  
  
3.  为接口创建新的 [COM\_INTERFACE\_ENTRY](../Topic/COM_INTERFACE_ENTRY%20\(ATL\).md)，如果项目被特性化，则添加 `coclass` 特性。  
  
4.  实现接口上的方法。  
  
## 请参阅  
 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)   
 [Visual C\+\+ 项目类型](../../ide/visual-cpp-project-types.md)   
 [使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)