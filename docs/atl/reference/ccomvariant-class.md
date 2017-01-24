---
title: "CComVariant Class | Microsoft Docs"
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
  - "ATL.CComVariant"
  - "ATL::CComVariant"
  - "CComVariant"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComVariant class"
  - "VARIANT macro"
  - "VARIANT macro, ATL"
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
caps.latest.revision: 26
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComVariant Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类包装 `VARIANT` 类型，提供指示数据类型的成员存储。  
  
## 语法  
  
```  
  
class CComVariant : public tagVARIANT  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComVariant::CComVariant](../Topic/CComVariant::CComVariant.md)|构造函数。|  
|[CComVariant::~CComVariant](../Topic/CComVariant::~CComVariant.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComVariant::Attach](../Topic/CComVariant::Attach.md)|附加 **VARIANT** 到 `CComVariant` 对象。|  
|[CComVariant::ChangeType](../Topic/CComVariant::ChangeType.md)|转换为新类型的 `CComVariant` 对象。|  
|[CComVariant::Clear](../Topic/CComVariant::Clear.md)|清除 `CComVariant` 对象。|  
|[CComVariant::Copy](../Topic/CComVariant::Copy.md)|复制 **VARIANT** 到 `CComVariant` 对象。|  
|[CComVariant::CopyTo](../Topic/CComVariant::CopyTo.md)|复制 `CComVariant` 对象的内容。|  
|[CComVariant::Detach](../Topic/CComVariant::Detach.md)|分离 `CComVariant` 对象的基础 **VARIANT**。|  
|[CComVariant::GetSize](../Topic/CComVariant::GetSize.md)|返回该范围总数 `CComVariant` 对象的内容的字节。|  
|[CComVariant::ReadFromStream](../Topic/CComVariant::ReadFromStream.md)|从流加载 **VARIANT**。|  
|[CComVariant::SetByRef](../Topic/CComVariant::SetByRef.md)|初始化 `CComVariant` 对象并将 **vt** 成员访问 **VT\_BYREF**。|  
|[CComVariant::WriteToStream](../Topic/CComVariant::WriteToStream.md)|保存基础 **VARIANT** 入流。|  
  
### 公共运算符  
  
|||  
|-|-|  
|[CComVariant::operator \<](../Topic/CComVariant::operator%20%3C.md)|指示 `CComVariant` 对象是否比指定的 **VARIANT**小于。|  
|[CComVariant::operator \>](../Topic/CComVariant::operator%20%3E.md)|指示 `CComVariant` 对象是否比指定的 **VARIANT**大。|  
|[运算符\! \=](../Topic/CComVariant::operator%20!=.md)|指示 `CComVariant` 对象是否不等于指定的 **VARIANT**。|  
|[运算符\=](../Topic/CComVariant::operator%20=.md)|赋值。`CComVariant` 对象。|  
|[运算符\=\=](../Topic/CComVariant::operator%20==.md)|指示 `CComVariant` 对象是否等于指定的 **VARIANT**。|  
  
## 备注  
 `CComVariant` 包装 `VARIANT and VARIANTARG` 类型，包括指示数据类型的联合和成员存储在该联合。  **VARIANT**的通常用于自动化。  
  
 `CComVariant` 从 **VARIANT** 类型派生的，所以可以使用它，实际上可以使用 **VARIANT**。  可以，例如，使用 **V\_VT** 宏提取 `CComVariant` 的类型或可以直接访问 **vt** 成员就可以与 **VARIANT**。  
  
## 继承层次结构  
 `tagVARIANT`  
  
 `CComVariant`  
  
## 要求  
 **Header:** atlcomcli.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)