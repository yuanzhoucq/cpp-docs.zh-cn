---
title: "adapter (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "<cliext/adapter>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<adapter> 标头 [STL/CLR]"
  - "<cliext/adapter> 标头 [STL/CLR]"
  - "适配器 [STL/CLR]"
ms.assetid: 71ce7e51-42b6-4f70-9595-303791a97677
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# adapter (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL\/CLR 标题 `<cliext/adapter>` 指定两个模板类 \(`collection_adapter` 和 `range_adapter`\) 以及 `make_collection`模板函数。  
  
## 语法  
  
```  
#include <cliext/adapter>  
```  
  
## 备注  
  
|类|说明|  
|-------|--------|  
|[collection\_adapter](../dotnet/collection-adapter-stl-clr.md)|包装基类库 \(BCL\) 设置为范围。|  
|[range\_adapter](../dotnet/range-adapter-stl-clr.md)|包装范围作为 BCL 集合。|  
  
|功能|说明|  
|--------|--------|  
|[make\_collection](../dotnet/make-collection-stl-clr.md)|使用某个迭代器对，范围创建适配器。|  
  
## 要求  
 **标头:** \<cliext\/adapter\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)