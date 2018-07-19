---
title: CComGITPtr 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
dev_langs:
- C++
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90da5e8394ea4f630a817b68edf60d4242b40be9
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884169"
---
# <a name="ccomgitptr-class"></a>CComGITPtr 类
此类提供用于处理接口指针的方法和全局接口表 (GIT)。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class CComGITPtr
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在 GIT 中的接口指针的类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CComGITPtr::CComGITPtr](#ccomgitptr)|构造函数。|  
|[CComGITPtr:: ~ CComGITPtr](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComGITPtr::Attach](#attach)|调用此方法以在全局接口表 (GIT) 中注册的接口指针。|  
|[CComGITPtr::CopyTo](#copyto)|调用此方法将接口从全局接口表 (GIT) 复制到传递的指针。|  
|[CComGITPtr::Detach](#detach)|调用此方法来取消关联的接口从`CComGITPtr`对象。|  
|[CComGITPtr::GetCookie](#getcookie)|调用此方法以返回从 cookie`CComGITPtr`对象。|  
|[CComGITPtr::Revoke](#revoke)|调用此方法以从全局接口表 (GIT) 中删除接口。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CComGITPtr::operator DWORD](#operator_dword)|返回从 cookie`CComGITPtr`对象。|  
|[CComGITPtr::operator =](#operator_eq)|赋值运算符。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Cookie。|  
  
## <a name="remarks"></a>备注  
 聚合自由线程封送处理程序，并需要使用从其他对象中获得的接口指针的对象必须采取额外步骤来确保正确封送的接口。 这通常涉及将接口指针存储在 GIT 并使用它每次从 GIT 获取指针。 类`CComGITPtr`提供可帮助你使用存储在 GIT 中的接口指针。  
  
> [!NOTE]
>  全局接口表工具才使用 DCOM 1.1 版 Windows 95 和更高版本、 Windows 98、 Windows NT 4.0 Service Pack 3 和更高版本和 Windows 2000 上可用。  
  
## <a name="requirements"></a>要求  
 **标头：** atlbase.h  
  
##  <a name="attach"></a>  CComGITPtr::Attach  
 调用此方法以在全局接口表 (GIT) 中注册的接口指针。  
  
```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```  
  
### <a name="parameters"></a>参数  
 *p*  
 要添加到 GIT 的接口指针。  
  
 *dwCookie*  
 用于标识的接口指针的 cookie。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 在调试版本中，如果 GIT 无效，或如果 cookie 为空，将会出错断言。  
  
##  <a name="ccomgitptr"></a>  CComGITPtr::CComGITPtr  
 构造函数。  
  
```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>参数  
 [in]*p*  
 要存储在全局接口表 (GIT) 中一个接口指针。  
  
 [in]*git*  
 向现有的引用`CComGITPtr`对象。  
  
 [in]*dwCookie*  
 一个用于标识的接口指针的 cookie。  
  
 [in]*rv*  
 源`CComGITPtr`对象移动中的数据。  
  
### <a name="remarks"></a>备注  
 创建一个新`CComGITPtr`对象，可以选择使用现有`CComGITPtr`对象。  
  
 构造函数利用*rv*是移动构造函数。 源中的数据移动数据*rv*，然后*rv*清除。  
  
##  <a name="dtor"></a>  CComGITPtr:: ~ CComGITPtr  
 析构函数。  
  
```
~CComGITPtr() throw();
```  
  
### <a name="remarks"></a>备注  
 从全局接口表 (GIT)，删除接口使用[CComGITPtr::Revoke](#revoke)。  
  
##  <a name="copyto"></a>  CComGITPtr::CopyTo  
 调用此方法将接口从全局接口表 (GIT) 复制到传递的指针。  
  
```
HRESULT CopyTo(T** pp) const throw();
```  
  
### <a name="parameters"></a>参数  
 *pp*  
 它将接收接口指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 从 GIT 接口复制到传递的指针。 当不再需要时，必须由调用方释放指针。  
  
##  <a name="detach"></a>  CComGITPtr::Detach  
 调用此方法来取消关联的接口从`CComGITPtr`对象。  
  
```
DWORD Detach() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回从 cookie`CComGITPtr`对象。  
  
### <a name="remarks"></a>备注  
 由调用方将删除从 GIT，该接口使用[CComGITPtr::Revoke](#revoke)。  
  
##  <a name="getcookie"></a>  CComGITPtr::GetCookie  
 调用此方法以返回从 cookie`CComGITPtr`对象。  
  
```
DWORD GetCookie() const;
```  
  
### <a name="return-value"></a>返回值  
 返回 cookie。  
  
### <a name="remarks"></a>备注  
 Cookie 是用于标识接口，并且其位置的变量。  
  
##  <a name="m_dwcookie"></a>  CComGITPtr::m_dwCookie  
 Cookie。  
  
```
DWORD m_dwCookie;
```  
  
### <a name="remarks"></a>备注  
 Cookie 是用于标识接口，并且其位置的成员变量。  
  
##  <a name="operator_eq"></a>  CComGITPtr::operator =  
 赋值运算符。  
  
```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>参数  
 [in]*p*  
 指向一个接口的指针。  
  
 [in]*git*  
 对 `CComGITPtr` 对象的引用。  
  
 [in]*dwCookie*  
 一个用于标识的接口指针的 cookie。  
  
 [in]*rv*  
 `CComGITPtr`移动中的数据。  
  
### <a name="return-value"></a>返回值  
 返回已更新`CComGITPtr`对象。  
  
### <a name="remarks"></a>备注  
 将一个新值赋给`CComGITPtr`对象，从现有对象或对全局接口表的引用。  
  
##  <a name="operator_dword"></a>  CComGITPtr::operator DWORD  
 返回与关联的 cookie`CComGITPtr`对象。  
  
```  
operator DWORD() const;
```  
  
### <a name="remarks"></a>备注  
 Cookie 是用于标识接口，并且其位置的变量。  
  
##  <a name="revoke"></a>  CComGITPtr::Revoke  
 调用此方法以从全局接口表 (GIT) 中删除当前接口。  
  
```
HRESULT Revoke() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 从 GIT 中删除接口。  
  
## <a name="see-also"></a>请参阅  
 [自由线程封送处理程序](../../atl/atl-and-the-free-threaded-marshaler.md)   
 [各个单元访问接口](http://msdn.microsoft.com/library/windows/desktop/ms682353)   
 [何时使用全局接口表](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [类概述](../../atl/atl-class-overview.md)
