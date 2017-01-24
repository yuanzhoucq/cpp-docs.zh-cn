---
title: "CComPtrBase Class | Microsoft Docs"
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
  - "ATL.CComPtrBase"
  - "ATL::CComPtrBase<T>"
  - "ATL.CComPtrBase<T>"
  - "ATL::CComPtrBase"
  - "CComPtrBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComPtrBase class"
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComPtrBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用基于COM的内存实例，此选件类为智能指针选件类提供基础。  
  
## 语法  
  
```  
  
      template <  
   class T   
> class CComPtrBase  
```  
  
#### 参数  
 `T`  
 智能指针将引用的对象类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComPtrBase::~CComPtrBase](../Topic/CComPtrBase::~CComPtrBase.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComPtrBase::Advise](../Topic/CComPtrBase::Advise.md)|调用此方法创建`CComPtrBase`的连接点和客户端的接收器之间的连接。|  
|[CComPtrBase::Attach](../Topic/CComPtrBase::Attach.md)|调用此方法将现有指针的所有权。|  
|[CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)|调用此方法创建选件类的对象与指定的选件类ID或程序ID.|  
|[CComPtrBase::CopyTo](../Topic/CComPtrBase::CopyTo.md)|调用此方法复制 `CComPtrBase` 指向另一个指针变量。|  
|[CComPtrBase::Detach](../Topic/CComPtrBase::Detach.md)|调用此方法释放指针的所有权。|  
|[CComPtrBase::IsEqualObject](../Topic/CComPtrBase::IsEqualObject.md)|调用此方法检查指定的 **IUnknown** 是否指向同一对象与 `CComPtrBase` 对象。|  
|[CComPtrBase::QueryInterface](../Topic/CComPtrBase::QueryInterface.md)|调用此方法返回指向一个指定的接口。|  
|[CComPtrBase::Release](../Topic/CComPtrBase::Release.md)|调用此方法释放接口。|  
|[CComPtrBase::SetSite](../Topic/CComPtrBase::SetSite.md)|调用此方法设置 `CComPtrBase` 对象的站点到父对象的 **IUnknown** 的。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CComPtrBase::operator T\*](../Topic/CComPtrBase::operator%20T*.md)|转换运算符。|  
|[CComPtrBase::operator \!](../Topic/CComPtrBase::operator%20!.md)|NOT 运算符。|  
|[CComPtrBase::operator &](../Topic/CComPtrBase::operator%20&.md)|& 运算符。|  
|[CComPtrBase::operator \*](../Topic/CComPtrBase::operator%20*.md)|\*运算符。|  
|[CComPtrBase::operator \<](../Topic/CComPtrBase::operator%20%3C.md)|小于运算符。|  
|[CComPtrBase::operator \=\=](../Topic/CComPtrBase::operator%20==.md)|相等运算符。|  
|[CComPtrBase::operator \-\>](../Topic/CComPtrBase::operator%20-%3E.md)|指向成员的指针运算符。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComPtrBase::p](../Topic/CComPtrBase::p.md)|指针数据成员变量。|  
  
## 备注  
 此选件类用于COM内存管理例程的其他智能指针提供基本类型，如 [CComQIPtr](../../atl/reference/ccomqiptr-class.md) 和 [CComPtr](../../atl/reference/ccomptr-class.md)。  派生类添加其构造函数和运算符，但是，取决于 `CComPtrBase`提供的方法。  
  
## 要求  
 **Header:** atlcomcli.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)