---
title: "IProvideClassInfo2Impl Class | Microsoft Docs"
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
  - "IProvideClassInfo2"
  - "ATL.IProvideClassInfo2Impl"
  - "IProvideClassInfo2Impl"
  - "ATL::IProvideClassInfo2Impl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "class information, ATL"
  - "IProvideClassInfo2 ATL implementation"
  - "IProvideClassInfo2Impl class"
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IProvideClassInfo2Impl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供 [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) 和 [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) 方法的默认实现。  
  
## 语法  
  
```  
  
      template <  
   const CLSID* pcoclsid,  
   const IID* psrcid,  
   const GUID* plibid = &CAtlModule::m_libid,  
   WORD wMajor = 1,  
   WORD wMinor = 0,  
   class tihclass = CComTypeInfoHolder   
>  
class ATL_NO_VTABLE IProvideClassInfo2Impl :  
   public IProvideClassInfo2  
```  
  
#### 参数  
 *pcoclsid*  
 为coclass的标识符的指针。  
  
 *psrcid*  
 对标识符的指针coclass的默认传出调度接口的。  
  
 `plibid`  
 对包含有关接口的信息的类型库的LIBID的指针。  默认情况下，该服务器级别的类型库通过。  
  
 `wMajor`  
 类型库的主版本。  默认值为 1。  
  
 `wMinor`  
 类型库的次版本。  默认值为 0。  
  
 `tihclass`  
 用于的选件类管理coclass的类型信息。  默认值为 `CComTypeInfoHolder`。  
  
## 成员  
  
### 构造函数  
  
|名称|说明|  
|--------|--------|  
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](../Topic/IProvideClassInfo2Impl::IProvideClassInfo2Impl.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IProvideClassInfo2Impl::GetClassInfo](../Topic/IProvideClassInfo2Impl::GetClassInfo.md)|检索 **ITypeInfo** 指向coclass的类型信息。|  
|[IProvideClassInfo2Impl::GetGUID](../Topic/IProvideClassInfo2Impl::GetGUID.md)|检索对象的传出调度接口的GUID。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[IProvideClassInfo2Impl::\_tih](../Topic/IProvideClassInfo2Impl::_tih.md)|管理coclass的类型信息。|  
  
## 备注  
 [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) 接口通过添加 `GetGUID` 方法扩展 [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303)。  此方法允许客户端检索其设置的默认事件的对象的输出接口的IID。  选件类 `IProvideClassInfo2Impl` 提供 **IProvideClassInfo** 和 `IProvideClassInfo2` 方法的默认实现。  
  
 `IProvideClassInfo2Impl` 包含托管coclass的类型信息的类型 `CComTypeInfoHolder` 的静态成员。  
  
## 继承层次结构  
 `IProvideClassInfo2`  
  
 `IProvideClassInfo2Impl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)