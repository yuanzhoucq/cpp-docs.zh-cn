---
title: CSecurityAttributes 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
dev_langs:
- C++
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bc37dd8025009e4f904373fc8aa106c93dc8210
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879329"
---
# <a name="csecurityattributes-class"></a>CSecurityAttributes 类
此类是安全的属性结构的精简包装。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
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
 `SECURITY_ATTRIBUTES`结构包含[安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa379561)用于创建对象并指定检索通过指定此结构的句柄是否可继承。  
  
 有关 Windows 中的访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)Windows SDK 中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `SECURITY_ATTRIBUTES`  
  
 `CSecurityAttributes`  
  
## <a name="requirements"></a>要求  
 **标头：** atlsecurity.h  
  
##  <a name="csecurityattributes"></a>  CSecurityAttributes::CSecurityAttributes  
 构造函数。  
  
```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *rSecurityDescriptor*  
 对安全描述符的引用。  
  
 *bInheritsHandle*  
 指定在创建新进程时是否继承返回的句柄。 如果此成员为 true，则新进程继承该句柄。  
  
##  <a name="set"></a>  Csecurityattributes:: Set  
 调用此方法以设置的属性`CSecurityAttributes`对象。  
  
```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```  
  
### <a name="parameters"></a>参数  
 *rSecurityDescriptor*  
 对安全描述符的引用。  
  
 *bInheritHandle*  
 指定在创建新进程时是否继承返回的句柄。 如果此成员为 true，则新进程继承该句柄。  
  
### <a name="remarks"></a>备注  
 构造函数使用此方法以初始化`CSecurityAttributes`对象。  
  
## <a name="see-also"></a>请参阅  
 [安全示例](../../visual-cpp-samples.md)   
 [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)   
 [安全描述符](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [类概述](../../atl/atl-class-overview.md)   
 [安全全局函数](../../atl/reference/security-global-functions.md)
