---
title: "包装类 | Microsoft Docs"
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
  - "ActiveX 控件 [C++], 包装类"
  - "数据绑定 [C++], ActiveX 控件"
  - "包装类 [C++], ActiveX 控件"
ms.assetid: ebbc17b9-cc1b-4c29-afa9-da7f9511876e
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 包装类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当 [插入控件](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md) 到 Visual C\+\+ 项目后，默认情况下不包括控件的包装类。  但是，如果要[修改控件的行为](../../data/ado-rdo/modifying-a-control-s-run-time-behavior.md)，可以为控件编写包装类。  可能需要为控件编写一个或多个包装类，具体取决于如何以编程方式操作控件。  
  
 包装类可用于控件类型库 \(.tlb\) 文件中的每个 coclass。  控件包装类的名称应是以字母 C 为前缀的控件名称。  
  
 有关包装类功能的更多信息，请参见控件基本技术的对象模型。  
  
 使用 [CWnd::GetDlgItem](../Topic/CWnd::GetDlgItem.md) 也要求包装类，因为返回值必须被转换为控件类。  例如：  
  
```  
CDBList* pDBList = 0;  
pDBList = static_cast<CDBList*>(GetDlgItem(IDC_DBLIST));  
```  
  
 通过读取生成的 .idl 文件，可以确定控件公开的属性、方法和事件，并直接查看方法和访问器函数声明。  使用 [OLE\/COM 对象查看器](../../data/ado-rdo/using-the-ole-com-object-viewer.md)可以从控件中获得附加信息。  
  
## 请参阅  
 [使用 ActiveX 控件](../../data/ado-rdo/using-activex-controls.md)   
 [修改控件的运行时行为](../../data/ado-rdo/modifying-a-control-s-run-time-behavior.md)