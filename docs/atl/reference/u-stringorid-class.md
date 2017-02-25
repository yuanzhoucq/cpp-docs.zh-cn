---
title: "_U_STRINGorID Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL._U_STRINGorID"
  - "ATL::_U_STRINGorID"
  - "_U_STRINGorID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_U_STRINGorID class"
  - "U_STRINGorID class"
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# _U_STRINGorID Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此参数适配器选件类允许资源名称\(`LPCTSTR`属于\)或资源ID \(**UINT**属于\)使用 **MAKEINTRESOURCE** 宏，将传递给函数，而无需调用方ID转换为字符串。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
class _U_STRINGorID  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[\_U\_STRINGorID::\_U\_STRINGorID](../Topic/_U_STRINGorID::_U_STRINGorID.md)|构造函数。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[\_U\_STRINGorID::m\_lpstr](../Topic/_U_STRINGorID::m_lpstr.md)|资源标识符。|  
  
## 备注  
 此选件类为实现对于Windows资源管理API包装的类型和 [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042)、 [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072)和 [LoadMenu](http://msdn.microsoft.com/library/windows/desktop/ms647990) 功能，接受 `LPCTSTR` 参数可以是资源的名称或其ID.  
  
 选件类定义两个构造函数重载:一 `LPCTSTR` 接受参数，另一个接受 **UINT** 参数。  **UINT** 参数转换为资源类型与Windows资源管理功能兼容使用在选件类的单个数据成员和结果存储的 **MAKEINTRESOURCE** 宏，[m\_lpstr](../Topic/_U_STRINGorID::m_lpstr.md)。  为 `LPCTSTR` 构造函数的参数存储直接，不进行转换。  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)