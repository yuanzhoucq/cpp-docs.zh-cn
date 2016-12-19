---
title: "使用 ADO 数据控件更新数据 | Microsoft Docs"
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
  - "ADO [C++], 数据绑定"
  - "ADO [C++], 数据控件"
ms.assetid: 8bec34b9-93dd-4872-b023-55ac011ccff5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 ADO 数据控件更新数据
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ADO 数据控件数据可以是只读的或可修改的。  
  
### 创建使用 ADO 数据控件修改数据的应用程序  
  
1.  设置 ADO 数据控件 **CursorLocation** 属性。  选项是：  
  
    -   服务器端  
  
    -   客户端  
  
2.  设置 ADO 数据控件 **LockType** 属性。  建议使用开放式并发。  
  
3.  设置 ADO 数据控件 **CursorType** 属性。  选项是：  
  
    -   键集游标  
  
    -   动态游标  
  
    -   静态游标  
  
     确保 OLE DB 提供程序支持所选选项。  
  
4.  根据需要设置数据绑定控件的属性以允许更新。  注意某些控件不允许更新。  
  
 有关这些属性的更多信息，请参见 ADO 文档。  
  
## 请参阅  
 [ADO 数据绑定](../../data/ado-rdo/ado-databinding.md)   
 [在 Visual C\+\+ 中使用 ADO 数据绑定](../../data/ado-rdo/using-ado-databinding-in-visual-cpp.md)