---
title: "IDispatchImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IDispatchImpl"
  - "ATL.IDispatchImpl"
  - "ATL::IDispatchImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "双重接口, 类"
  - "ATL 中的 IDispatch 类支持"
  - "IDispatchImpl 类"
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
caps.latest.revision: 27
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDispatchImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为双重接口的 `IDispatch` 部件提供默认实现。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
template<  
   class T,  
   const IID* piid= &__uuidof(T),  
   const GUID* plibid = &CAtlModule::m_libid,  
   WORD wMajor = 1,  
   WORD wMinor = 0,  
   class tihclass = CComTypeInfoHolder   
>   
class ATL_NO_VTABLE IDispatchImpl :  
   public T  
```  
  
#### 参数  
 \[in\] `T`  
 双绑定接口。  
  
 \[in\] `piid`  
 为 `T`IID的指针。  
  
 \[in\] `plibid`  
 对包含有关接口的信息的类型库的LIBID的指针。  默认情况下，该服务器级别的类型库通过。  
  
 \[in\] `wMajor`  
 类型库的主版本。  默认情况下，该值为 1。  
  
 \[in\] `wMinor`  
 类型库的次版本。  默认情况下，该值为 0。  
  
 \[in\] `tihclass`  
 用于的选件类管理 `T`的类型信息。  默认情况下，此值为 `CComTypeInfoHolder`。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[IDispatchImpl::IDispatchImpl](../Topic/IDispatchImpl::IDispatchImpl.md)|构造函数。  调用管理双重接口的类型信息的受保护成员变量的 `AddRef`。  调用析构函数 `Release`。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IDispatchImpl::GetIDsOfNames](../Topic/IDispatchImpl::GetIDsOfNames.md)|将一组名称映射为对应的一组调度标识符。|  
|[IDispatchImpl::GetTypeInfo](../Topic/IDispatchImpl::GetTypeInfo.md)|检索双重接口的类型信息。|  
|[IDispatchImpl::GetTypeInfoCount](../Topic/IDispatchImpl::GetTypeInfoCount.md)|确定是否有类型信息提供为双绑定接口。|  
|[IDispatchImpl::Invoke](../Topic/IDispatchImpl::Invoke.md)|提供了对双绑定接口公开的方法和属性。|  
  
## 备注  
 `IDispatchImpl` 为所有双重接口的 `IDispatch` 部件提供默认实现在对象。  双重接口从 `IDispatch` 派生并仅使用自动化的类型。  与调度接口，双重接口支持早期绑定和后期绑定;但是，双重接口还支持vtable绑定。  
  
 下面的示例演示 `IDispatchImpl` 的典型实现。  
  
 [!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/CPP/idispatchimpl-class_1.h)]  
  
 默认情况下，`IDispatchImpl` 选件类用于在注册表中 `T` 查找该类型信息。  若要实现注销的接口，可以使用 `IDispatchImpl` 选件类，而无需访问注册表使用预定义的版本号。  如果创建具有0xFFFF作为 `wMajor` 的值和0xFFFF作为 `wMinor`的值的一 `IDispatchImpl` 对象，`IDispatchImpl` 选件类从.dll文件检索该类型库而不是注册表。  
  
 `IDispatchImpl` 包含管理双重接口的类型信息类型 `CComTypeInfoHolder` 的静态成员。  如果您具有实现同一双重接口的多个对象，因此，只有使用 `CComTypeInfoHolder` 一个实例。  
  
## 继承层次结构  
 `T`  
  
 `IDispatchImpl`  
  
## 要求  
 **标头:** atlcom.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)