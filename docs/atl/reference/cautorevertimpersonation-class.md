---
title: "CAutoRevertImpersonation 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
dev_langs: C++
helpviewer_keywords: CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b1982fc3c8b0d46dfd636cab63be82509fa07f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation 类
此类将恢复[CAccessToken](../../atl/reference/caccesstoken-class.md) nonimpersonating 状态时超出范围的对象。  
  
## <a name="syntax"></a>语法  
  
```
class CAutoRevertImpersonation
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|构造`CAutoRevertImpersonation`对象|  
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|销毁对象，并将恢复访问令牌模拟。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAutoRevertImpersonation::Attach](#attach)|自动执行访问令牌模拟恢复。|  
|[CAutoRevertImpersonation::Detach](#detach)|取消自动模拟恢复。|  
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|检索访问令牌当前与此对象关联。|  
  
## <a name="remarks"></a>备注  
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909)是一个对象，用于描述进程或线程的安全上下文，并分配给每个用户登录到 Windows NT 或 Windows 2000 的系统。 这些访问令牌可以用来表示`CAccessToken`类。  
  
 另外，有时需要模拟访问令牌。 此类提供为方便起见，但它不执行模拟的访问令牌;它仅执行到 nonimpersonated 状态自动恢复。 这是因为可以通过多种不同的方式执行访问令牌模拟。  
  
 有关 Windows 中的访问控制模型的简介，请参阅[访问控制](http://msdn.microsoft.com/library/windows/desktop/aa374860)Windows SDK 中。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlsecurity.h  
  
##  <a name="attach"></a>CAutoRevertImpersonation::Attach  
 自动执行访问令牌模拟恢复。  
  
```
void Attach(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>参数  
 `pAT`  
 地址[CAccessToken](../../atl/reference/caccesstoken-class.md)对象将自动恢复  
  
### <a name="remarks"></a>备注  
 应仅使用此方法，如果[CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md)对象创建与 NULL`CAccessToken`指针，或如果[分离](#detach)以前调用过。 对于简单的情况下，不需要使用此方法。  
  
##  <a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation  
 构造 `CAutoRevertImpersonation` 对象。  
  
```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>参数  
 `pAT`  
 地址[CAccessToken](../../atl/reference/caccesstoken-class.md)对象将自动恢复。  
  
### <a name="remarks"></a>备注  
 从和最好是在创建之前应单独执行访问令牌实际模拟`CAutoRevertImpersonation`对象。 此模拟将恢复自动当`CAutoRevertImpersonation`对象超出范围。  
  
##  <a name="dtor"></a>CAutoRevertImpersonation:: ~ CAutoRevertImpersonation  
 销毁对象，并将恢复访问令牌模拟。  
  
```
~CAutoRevertImpersonation() throw();
```  
  
### <a name="remarks"></a>备注  
 将恢复当前有效的任何模拟[CAccessToken](../../atl/reference/caccesstoken-class.md)提供可以在构造或通过对象[附加](#attach)方法。 如果没有`CAccessToken`是相关联，析构函数不起作用。  
  
##  <a name="detach"></a>CAutoRevertImpersonation::Detach  
 取消自动模拟恢复。  
  
```
const CAccessToken* Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 先前相关联的地址[CAccessToken](../../atl/reference/caccesstoken-class.md)，如果没有关联存在则为 NULL。  
  
### <a name="remarks"></a>备注  
 调用**分离**阻止`CAutoRevertImpersonation`对象从恢复当前有效的任何模拟[CAccessToken](../../atl/reference/caccesstoken-class.md)与此对象关联的对象。 `CAutoRevertImpersonation`然后可以通过不起作用销毁或它们重新关联到相同或另一个`CAccessToken`对象使用[附加](#attach)。  
  
##  <a name="getaccesstoken"></a>CAutoRevertImpersonation::GetAccessToken  
 检索访问令牌当前与此对象关联。  
  
```
const CAccessToken* GetAccessToken() throw();
```  
  
### <a name="return-value"></a>返回值  
 先前相关联的地址[CAccessToken](../../atl/reference/caccesstoken-class.md)，如果没有关联存在则为 NULL。  
  
### <a name="remarks"></a>备注  
 如果此方法出于包括的模拟的恢复的目的称为`CAccessToken`对象，[分离](#detach)应改为使用方法。  
  
## <a name="see-also"></a>请参阅  
 [ATLSecurity 示例](../../visual-cpp-samples.md)   
 [访问令牌](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [类概述](../../atl/atl-class-overview.md)
