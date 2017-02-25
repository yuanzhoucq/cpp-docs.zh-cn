---
title: "CComGITPtr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComGITPtr<T>"
  - "CComGITPtr"
  - "ATL.CComGITPtr"
  - "ATL.CComGITPtr<T>"
  - "ATL::CComGITPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComGITPtr class"
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComGITPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为相关的方法接口指针和全局接口表\(GIT）。  
  
## 语法  
  
```  
  
      template <  
   class T   
>  
class CComGITPtr  
```  
  
#### 参数  
 `T`  
 在GIT要存储的接口指针的类型。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CComGITPtr::CComGITPtr](../Topic/CComGITPtr::CComGITPtr.md)|构造函数。|  
|[CComGITPtr::~CComGITPtr](../Topic/CComGITPtr::~CComGITPtr.md)|该析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CComGITPtr::Attach](../Topic/CComGITPtr::Attach.md)|调用此方法注册接口指针在全局接口表\(GIT\)中。|  
|[CComGITPtr::CopyTo](../Topic/CComGITPtr::CopyTo.md)|调用此方法将全局接口表\(GIT\)的接口添加到传递的指针。|  
|[CComGITPtr::Detach](../Topic/CComGITPtr::Detach.md)|调用此方法分离 `CComGITPtr` 对象的接口。|  
|[CComGITPtr::GetCookie](../Topic/CComGITPtr::GetCookie.md)|调用此方法返回从 `CComGITPtr` 对象的cookie。|  
|[CComGITPtr::Revoke](../Topic/CComGITPtr::Revoke.md)|调用此方法从全局接口表\(GIT\)移除接口。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CComGITPtr::operator DWORD](../Topic/CComGITPtr::operator%20DWORD.md)|返回从 `CComGITPtr` 对象的cookie。|  
|[CComGITPtr::operator \=](../Topic/CComGITPtr::operator%20=.md)|赋值运算符。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CComGITPtr::m\_dwCookie](../Topic/CComGITPtr::m_dwCookie.md)|cookie。|  
  
## 备注  
 Objects复合自由线程封送拆收器和需要使用的其他对象获取的接口指针必须执行附加步骤以确保接口正确封送。  通常，每次使用，则与存储接口指针在GIT和获取指针从GIT它。  提供选件类 `CComGITPtr` 帮助您在GIT存储的接口指针。  
  
> [!NOTE]
>  全局接口表计算机只有在具有DCOM 1.1版和更高版本中，Windows 98、Windows NT 4.0 Service Pack 3和更高版本以及Windows 2000的Windows 95。  
  
## 要求  
 **Header:** atlbase.h  
  
## 请参阅  
 [自由线程封送拆收器](../../atl/atl-and-the-free-threaded-marshaler.md)   
 [Accessing Interfaces Across Apartments](http://msdn.microsoft.com/library/windows/desktop/ms682353)   
 [When to Use the Global Interface Table](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Class Overview](../../atl/atl-class-overview.md)