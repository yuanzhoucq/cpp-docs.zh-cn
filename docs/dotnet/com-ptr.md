---
title: "com::ptr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "com::ptr"
ms.assetid: ee302e3c-8fed-4875-a372-2e55003718d3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# com::ptr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可用作类的 CLR 成员的 COM 对象的包装。  其析构函数调用时，也会自动包装 COM 对象生存期管理，在释放对象自己的引用。  类似于 [CComPtr Class](../atl/reference/ccomptr-class.md)。  
  
## 语法  
  
```  
#include <msclr\com\ptr.h>  
```  
  
## 备注  
 在[com::ptr 类](../dotnet/com-ptr-class.md) msclr \<\\ \\ ptr.h com 定义文件\>。  
  
## 请参阅  
 [C\+\+ 支持库](../dotnet/cpp-support-library.md)