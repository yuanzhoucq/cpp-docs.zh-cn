---
title: "CAutoRevertImpersonation 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
dev_langs:
- C++
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: f86f1e5067583b3c4c615c8ca3095e8b67b3fffe
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation 类
此类将还原[CAccessToken](../../atl/reference/caccesstoken-class.md) nonimpersonating 状态时超出范围的对象。  
  
## <a name="syntax"></a>语法  
  
```
class CAutoRevertImpersonation
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|构造`CAutoRevertImpersonation`对象|  
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|销毁对象，并恢复访问令牌模拟。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAutoRevertImpersonation::Attach](#attach)|自动执行一个访问令牌模拟重新。|  
|[CAutoRevertImpersonation::Detach](#detach)|取消自动模拟重新。|  
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|检索与此对象关联的访问令牌当前。|  
  
## <a name="remarks"></a>备注  
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909)是一个对象，描述进程或线程的安全上下文，并分配给每个用户登录到 Windows NT 或 Windows 2000 的系统。 这些访问令牌可以用来表示`CAccessToken`类。  
  
 此外，有时需要模拟访问令牌。 为方便起见，提供此类，但它不执行模拟的访问令牌;它仅执行到 nonimpersonated 状态自动恢复。 这是因为可以执行多种不同的方法的访问令牌模拟。  
  
 在 Windows 访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlsecurity.h  
  
##  <a name="attach"></a>CAutoRevertImpersonation::Attach  
 自动执行一个访问令牌模拟重新。  
  
```
void Attach(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>参数  
 `pAT`  
 地址[CAccessToken](../../atl/reference/caccesstoken-class.md)对象会自动恢复  
  
### <a name="remarks"></a>备注  
 如果应仅使用此方法[CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md)对象使用空值创建`CAccessToken`指针，或者如果[分离](#detach)以前调用过。 对于简单情况，不需要使用此方法。  
  
##  <a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation  
 构造 `CAutoRevertImpersonation` 对象。  
  
```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>参数  
 `pAT`  
 地址[CAccessToken](../../atl/reference/caccesstoken-class.md)对象会自动恢复。  
  
### <a name="remarks"></a>备注  
 从和最好的创建之前应该分别执行访问令牌的实际模拟`CAutoRevertImpersonation`对象。 此模拟会自动还原时`CAutoRevertImpersonation`对象超出范围。  
  
##  <a name="dtor"></a>CAutoRevertImpersonation:: ~ CAutoRevertImpersonation  
 销毁对象，并恢复访问令牌模拟。  
  
```
~CAutoRevertImpersonation() throw();
```  
  
### <a name="remarks"></a>备注  
 将恢复当前有效的任何模拟[CAccessToken](../../atl/reference/caccesstoken-class.md)提供可以在构造或通过对象[附加](#attach)方法。 如果没有`CAccessToken`是相关联，析构函数不起作用。  
  
##  <a name="detach"></a>CAutoRevertImpersonation::Detach  
 取消自动模拟重新。  
  
```
const CAccessToken* Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 以前相关联的地址[CAccessToken](../../atl/reference/caccesstoken-class.md)，或如果没有关联已存在，则为 NULL。  
  
### <a name="remarks"></a>备注  
 调用**分离**可防止`CAutoRevertImpersonation`对象从还原的任何模拟当前作用于[CAccessToken](../../atl/reference/caccesstoken-class.md)与此对象关联的对象。 `CAutoRevertImpersonation`然后可以通过不起作用销毁或重新关联到相同或另一个`CAccessToken`对象使用[附加](#attach)。  
  
##  <a name="getaccesstoken"></a>CAutoRevertImpersonation::GetAccessToken  
 检索与此对象关联的访问令牌当前。  
  
```
const CAccessToken* GetAccessToken() throw();
```  
  
### <a name="return-value"></a>返回值  
 以前相关联的地址[CAccessToken](../../atl/reference/caccesstoken-class.md)，或如果没有关联已存在，则为 NULL。  
  
### <a name="remarks"></a>备注  
 如果此方法调用包括的模拟重新出于`CAccessToken`对象，[分离](#detach)应改为使用方法。  
  
## <a name="see-also"></a>另请参阅  
 [ATLSecurity 示例](../../visual-cpp-samples.md)   
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [类概述](../../atl/atl-class-overview.md)

