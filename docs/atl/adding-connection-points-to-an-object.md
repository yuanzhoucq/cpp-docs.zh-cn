---
title: "Adding Connection Points to an Object | Microsoft Docs"
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
helpviewer_keywords: 
  - "连接点 [C++], 添加到 ATL 对象"
  - "Implement Connection Point ATL wizard"
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Connection Points to an Object
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[ATL教程](../atl/active-template-library-atl-tutorial.md) 演示如何创建控件与支持连接点，如何将事件，然后如何实现连接点。  ATL实现连接点用于 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 选件类。  
  
 实现连接点，有两种选择:  
  
-   实现自己发出的事件源，通过添加连接点对控件或对象。  
  
-   重新使用连接点在另一个类型定义的接口库。  
  
 在任何情况下，实现连接点向导"使用类型库完成其工作。  
  
### 若要添加连接点对控件或对象  
  
1.  在库中定义的调度接口块.idl文件。  如果启用了支持连接点何时使用ATL控件向导"创建了控件，调度接口已经创建。  如果未启用支持连接点您在创建控件时，必须手动添加、加到.idl文件。  下面是调度接口的示例。  不需要输出接口是调度接口，但许多脚本语言\(如VBScript和JScript需要此，因此，此示例使用两调度接口:  
  
     [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/CPP/adding-connection-points-to-an-object_1.idl)]  
  
     使用该uuidgen.exe或guidgen.exe实用工具生成GUID。  
  
2.  添加调度接口为coclass的 `[default,source]` 接口在项目的.idl文件的对象的。  同样，因此，如果启用了支持连接点您在创建了控件，ATL控件向导将创建 `[default,source`\]项。  手动添加此项，请添加以粗体行:  
  
     [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/CPP/adding-connection-points-to-an-object_2.idl)]  
  
     有关示例参见。[Circ](../top/visual-cpp-samples.md) ATL示例的.idl文件。  
  
3.  使用选件类视图将方法和属性添加到事件接口。  右击"选件类视图的选件类，指向在快捷菜单上的 **Add**，然后单击 **AddConnection Point**。  
  
4.  在 **Source Interfaces** 实现的列表框连接点向导中，选择 **Project's interfaces**。  如果您选择控件的接口并按 **OK**，则将:  
  
    -   生成具有实现代码将创建为事件出站的事件代理选件类的一个标头文件。  
  
    -   将项添加到连接点映射。  
  
     您还会看到所有的列出了计算机上的类型库。  如果要实现确切在另一个类型找到具有相同输出接口库，则应只使用其中一个其他类型库定义自己的连接点。  
  
### 若要重新使用连接点在另一个类型定义的接口库  
  
1.  在选件类视图中，右击实现一 **BEGIN\_COM\_MAP** 宏的选件类，指向在快捷菜单上的 **Add**，然后单击 **AddConnection Point**。  
  
2.  在实现连接点向导中，选择在类型库中的类型库和接口并单击 **Add**。  
  
3.  编辑.idl文件为:  
  
    -   复制调度接口从使用事件源的对象的.idl文件。  
  
    -   使用该类型库的 **importlib** 命令。  
  
## 请参阅  
 [连接点](../atl/atl-connection-points.md)