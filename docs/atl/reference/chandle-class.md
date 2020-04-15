---
title: CHandle 类
ms.date: 07/09/2019
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
ms.openlocfilehash: 7c72ded75298ed69efe73c1a81abf404545ea9b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326927"
---
# <a name="chandle-class"></a>CHandle 类

此类提供了创建和使用句柄对象的方法。

## <a name="syntax"></a>语法

```
class CHandle
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[操作：：CHandle](#chandle)|构造函数。|
|[操作：：*CHandle](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[操作：：附加](#attach)|调用此方法将`CHandle`对象附加到现有句柄。|
|[操作：关闭](#close)|调用此方法以关闭对象`CHandle`。|
|[查德：:D塔奇](#detach)|调用此方法以从`CHandle`对象分离句柄。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[操作：：操作员操作](#operator_handle)|返回存储句柄的值。|
|[操作：：运算符 |](#operator_eq)|赋值运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[操作：：m_h](#m_h)|存储句柄的成员变量。|

## <a name="remarks"></a>备注

每当`CHandle`需要句柄时，都可以使用对象：主要区别是该`CHandle`对象将自动删除。

> [!NOTE]
> 某些 API 函数将使用 NULL 作为空句柄或无效句柄，而其他函数则使用INVALID_HANDLE_VALUE。 `CHandle`仅使用 NULL，并将INVALID_HANDLE_VALUE视为真正的句柄。 如果调用可以返回INVALID_HANDLE_VALUE的 API，则应在调用[CHandle：：附加](#attach)或传递给`CHandle`构造函数之前检查此值，然后传递 NULL。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="chandleattach"></a><a name="attach"></a>操作：：附加

调用此方法将`CHandle`对象附加到现有句柄。

```
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>参数

*H*<br/>
`CHandle`将取得句柄*h*的所有权。

### <a name="remarks"></a>备注

将`CHandle`对象分配给*h*句柄，然后调用**h.detach（）**。 在调试生成中，如果*h*为 NULL，将引发 ATLASSERT。 没有对手柄的有效性进行其他检查。

## <a name="chandlechandle"></a><a name="chandle"></a>操作：：CHandle

构造函数。

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>参数

*H*<br/>
现有句柄 或`CHandle`。

### <a name="remarks"></a>备注

创建新`CHandle`对象，可以选择使用现有句柄或`CHandle`对象。

## <a name="chandlechandle"></a><a name="dtor"></a>操作：：*CHandle

析构函数。

```
~CHandle() throw();
```

### <a name="remarks"></a>备注

通过调用`CHandle`[CHandle：：关闭](#close)来释放对象。

## <a name="chandleclose"></a><a name="close"></a>操作：关闭

调用此方法以关闭对象`CHandle`。

```
void Close() throw();
```

### <a name="remarks"></a>备注

关闭打开的对象句柄。 如果句柄为 NULL（如果`Close`已调用，则为 NULL，则将在调试生成中引发 ATLASSERT）。

## <a name="chandledetach"></a><a name="detach"></a>查德：:D塔奇

调用此方法以从`CHandle`对象分离句柄。

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>返回值

返回要分离的句柄。

### <a name="remarks"></a>备注

释放句柄的所有权。

## <a name="chandlem_h"></a><a name="m_h"></a>操作：：m_h

存储句柄的成员变量。

```
HANDLE m_h;
```

## <a name="chandleoperator-"></a><a name="operator_eq"></a>操作：：运算符 |

分配运算符。

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>参数

*H*<br/>
`CHandle`将取得句柄*h*的所有权。

### <a name="return-value"></a>返回值

返回对新`CHandle`对象的引用。

### <a name="remarks"></a>备注

如果`CHandle`对象当前包含句柄，它将关闭。 传入`CHandle`的对象的句柄引用集 NULL。 这可确保两`CHandle`个对象永远不会包含相同的活动句柄。

## <a name="chandleoperator-handle"></a><a name="operator_handle"></a>操作：：操作员操作

返回存储句柄的值。

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>备注

返回存储在[CHandle：：m_h](#m_h)中的值。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
