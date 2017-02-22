---
title: "_U_RECT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::_U_RECT"
  - "_U_RECT"
  - "ATL._U_RECT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_U_RECT class"
  - "U_RECT class"
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# _U_RECT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此参数适配器选件类允许 `RECT` 指针或引用传递给实现基于指针的函数。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class _U_RECT  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[\_U\_RECT::\_U\_RECT](../Topic/_U_RECT::_U_RECT.md)|构造函数。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[\_U\_RECT::m\_lpRect](../Topic/_U_RECT::m_lpRect.md)|为 `RECT`的指针。|  
  
## 备注  
 选件类定义两个构造函数重载:一 **RECT&** 接受参数，另一个接受 `LPRECT` 参数。  第一个构造函数在选件类的单个数据成员，[m\_lpRect](../Topic/_U_RECT::m_lpRect.md)存储引用参数的地址。  指向构造函数的参数存储直接，不进行转换。  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)