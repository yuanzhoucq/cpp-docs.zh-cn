---
title: "CSecurityAttributes 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
dev_langs: C++
helpviewer_keywords: CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 918f90c9f04736eb2328d989e21b7b9997edab86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="csecurityattributes-class"></a>CSecurityAttributes 类
此类是安全特性结构的瘦包装器。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Csecurityattributes:: Set](#set)|调用此方法以设置的属性`CSecurityAttributes`对象。|  
  
## <a name="remarks"></a>备注  
 **SECURITY_ATTRIBUTES**结构包含[安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa379561)用于创建对象，并指定通过指定此结构来检索句柄是否可继承。  
  
 有关 Windows 中的访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)Windows SDK 中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `SECURITY_ATTRIBUTES`  
  
 `CSecurityAttributes`  
  
## <a name="requirements"></a>惠?  
 **标头：** atlsecurity.h  
  
##  <a name="csecurityattributes"></a>CSecurityAttributes::CSecurityAttributes  
 构造函数。  
  
```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rSecurityDescriptor`  
 对安全描述符的引用。  
  
 `bInheritsHandle`  
 指定在创建新进程时是否继承返回的句柄。 如果此成员为 true，则新进程继承该句柄。  
  
##  <a name="set"></a>Csecurityattributes:: Set  
 调用此方法以设置的属性`CSecurityAttributes`对象。  
  
```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `rSecurityDescriptor`  
 对安全描述符的引用。  
  
 `bInheritHandle`  
 指定在创建新进程时是否继承返回的句柄。 如果此成员为 true，则新进程继承该句柄。  
  
### <a name="remarks"></a>备注  
 此方法用于构造函数初始化`CSecurityAttributes`对象。  
  
## <a name="see-also"></a>请参阅  
 [安全示例](../../visual-cpp-samples.md)   
 [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)   
 [安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全全局函数](../../atl/reference/security-global-functions.md)
