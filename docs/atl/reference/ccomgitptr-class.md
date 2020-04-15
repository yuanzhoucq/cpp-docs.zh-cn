---
title: CComGITPtr 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
ms.openlocfilehash: 230eeb1577189d2057e530e1df8ef99c611fb32b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327843"
---
# <a name="ccomgitptr-class"></a>CComGITPtr 类

此类提供了处理接口指针和全局接口表 （GIT） 的方法。

## <a name="syntax"></a>语法

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在 GIT 中的接口指针的类型。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComGITPtr：CComGITPtr](#ccomgitptr)|构造函数。|
|[CComGITPtr：*CComGITPtr](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CComGITPtr：：附加](#attach)|调用此方法以在全局接口表 （GIT） 中注册接口指针。|
|[CComGITPtr：：复制到](#copyto)|调用此方法以将接口从全局接口表 （GIT） 复制到传递的指针。|
|[CComGITPtr：:D埃塔奇](#detach)|调用此方法以取消接口与`CComGITPtr`对象的关联。|
|[CComGITPtr：获取饼干](#getcookie)|调用此方法以从`CComGITPtr`对象返回 Cookie。|
|[CComGITPtr：撤销](#revoke)|调用此方法从全局接口表 （GIT） 中删除接口。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CComGITPtr：：操作员DWORD](#operator_dword)|从`CComGITPtr`对象返回 Cookie。|
|[CComGITPtr：：运算符 |](#operator_eq)|赋值运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComGITPtr：m_dwCookie](#m_dwcookie)|饼干|

## <a name="remarks"></a>备注

聚合自由线程封送器且需要使用从其他对象获取的接口指针的对象必须采取额外步骤，以确保接口正确封送。 这通常涉及将接口指针存储在 GIT 中，并在每次使用时从 GIT 获取指针。 提供该`CComGITPtr`类是为了帮助您使用存储在 GIT 中的接口指针。

> [!NOTE]
> 全局接口表功能仅在 Windows 95 上提供 DCOM 版本 1.1 及更高版本、Windows 98、Windows NT 4.0 和 Service Pack 3 及更高版本。Windows 2000。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="ccomgitptrattach"></a><a name="attach"></a>CComGITPtr：：附加

调用此方法以在全局接口表 （GIT） 中注册接口指针。

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>参数

*P*<br/>
要添加到 GIT 的接口指针。

*dwCookie*<br/>
用于标识接口指针的 Cookie。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

在调试生成中，如果 GIT 无效，或者如果 Cookie 等于 NULL，则会发生断言错误。

## <a name="ccomgitptrccomgitptr"></a><a name="ccomgitptr"></a>CComGITPtr：CComGITPtr

构造函数。

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>参数

*P*<br/>
[在]要存储在全局接口表 （GIT） 中的接口指针。

*Git*<br/>
[在]对现有`CComGITPtr`对象的引用。

*dwCookie*<br/>
[在]用于标识接口指针的 Cookie。

*Rv*<br/>
[在]要从`CComGITPtr`中移动数据的源对象。

### <a name="remarks"></a>备注

创建新`CComGITPtr`对象，可以选择使用现有`CComGITPtr`对象。

使用*rv*的构造函数是移动构造函数。 数据从源*rv*移动，然后*清除 rv。*

## <a name="ccomgitptrccomgitptr"></a><a name="dtor"></a>CComGITPtr：*CComGITPtr

析构函数。

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>备注

使用[CComGITPtr：：：revoke](#revoke)，从全局接口表 （GIT） 中删除接口。

## <a name="ccomgitptrcopyto"></a><a name="copyto"></a>CComGITPtr：：复制到

调用此方法以将接口从全局接口表 （GIT） 复制到传递的指针。

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>参数

*Pp*<br/>
接收接口的指针。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

从 GIT 的接口复制到传递的指针。 当不再需要指针时，调用方必须释放该指针。

## <a name="ccomgitptrdetach"></a><a name="detach"></a>CComGITPtr：:D埃塔奇

调用此方法以取消接口与`CComGITPtr`对象的关联。

```
DWORD Detach() throw();
```

### <a name="return-value"></a>返回值

从`CComGITPtr`对象返回 Cookie。

### <a name="remarks"></a>备注

调用方使用[CComGITPtr：：：：revoke，](#revoke)由调用方从 GIT 中删除接口。

## <a name="ccomgitptrgetcookie"></a><a name="getcookie"></a>CComGITPtr：获取饼干

调用此方法以从`CComGITPtr`对象返回 Cookie。

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>返回值

返回 Cookie。

### <a name="remarks"></a>备注

Cookie 是用于标识接口及其位置的变量。

## <a name="ccomgitptrm_dwcookie"></a><a name="m_dwcookie"></a>CComGITPtr：m_dwCookie

饼干

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>备注

Cookie 是用于标识接口及其位置的成员变量。

## <a name="ccomgitptroperator-"></a><a name="operator_eq"></a>CComGITPtr：：运算符 |

分配运算符。

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>参数

*P*<br/>
[在]指向接口的指针。

*Git*<br/>
[在]对对象的引用`CComGITPtr`。

*dwCookie*<br/>
[在]用于标识接口指针的 Cookie。

*Rv*<br/>
[在]`CComGITPtr`要移动数据。

### <a name="return-value"></a>返回值

返回更新`CComGITPtr`的对象。

### <a name="remarks"></a>备注

从现有`CComGITPtr`对象或从引用到全局接口表向对象分配新值。

## <a name="ccomgitptroperator-dword"></a><a name="operator_dword"></a>CComGITPtr：：操作员DWORD

返回与`CComGITPtr`对象关联的 Cookie。

```
operator DWORD() const;
```

### <a name="remarks"></a>备注

Cookie 是用于标识接口及其位置的变量。

## <a name="ccomgitptrrevoke"></a><a name="revoke"></a>CComGITPtr：撤销

调用此方法从全局接口表 （GIT） 中删除当前接口。

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

从 GIT 中删除接口。

## <a name="see-also"></a>另请参阅

[自由线程封送拆收器](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[跨公寓访问接口](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[何时使用全局接口表](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[类概述](../../atl/atl-class-overview.md)
