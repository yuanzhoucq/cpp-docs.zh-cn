---
title: CD2DResource 类
ms.date: 03/27/2019
f1_keywords:
- CD2DResource
- AFXRENDERTARGET/CD2DResource
- AFXRENDERTARGET/CD2DResource::CD2DResource
- AFXRENDERTARGET/CD2DResource::Create
- AFXRENDERTARGET/CD2DResource::Destroy
- AFXRENDERTARGET/CD2DResource::IsValid
- AFXRENDERTARGET/CD2DResource::IsAutoDestroy
- AFXRENDERTARGET/CD2DResource::ReCreate
- AFXRENDERTARGET/CD2DResource::m_bIsAutoDestroy
- AFXRENDERTARGET/CD2DResource::m_pParentTarget
helpviewer_keywords:
- CD2DResource [MFC], CD2DResource
- CD2DResource [MFC], Create
- CD2DResource [MFC], Destroy
- CD2DResource [MFC], IsValid
- CD2DResource [MFC], IsAutoDestroy
- CD2DResource [MFC], ReCreate
- CD2DResource [MFC], m_bIsAutoDestroy
- CD2DResource [MFC], m_pParentTarget
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
ms.openlocfilehash: 5e747eda42e625d0f4cf65859e471933bbb043ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369098"
---
# <a name="cd2dresource-class"></a>CD2DResource 类

提供用于创建和管理 D2D 资源（如画笔、图层和文本）的接口的抽象类。

## <a name="syntax"></a>语法

```
class CD2DResource : public CObject;
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CD2D 资源：CD2D 资源](#cd2dresource)|构造 CD2D 资源对象。|
|[CD2D 资源：*CD2D 资源](#_dtorcd2dresource)|析构函数。 销毁 D2D 资源对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2D 资源：创建](#create)|创建 CD2D 资源。|
|[CD2D资源：:D](#destroy)|销毁 CD2D 资源对象。|
|[CD2D 资源：有效](#isvalid)|检查资源有效性|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CD2D 资源：：自动销毁](#isautodestroy)|检查自动销毁标志。|
|[CD2D 资源：重新创建](#recreate)|重新创建 CD2D 资源。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2D 资源：m_bIsAutoDestroy](#m_bisautodestroy)|资源将被所有者销毁 （CRenderTarget）|
|[CD2D 资源：m_pParentTarget](#m_pparenttarget)|指向父 CRenderTarget 的指针）|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dresourcecd2dresource"></a><a name="_dtorcd2dresource"></a>CD2D 资源：*CD2D 资源

析构函数。 销毁 D2D 资源对象时调用。

```
virtual ~CD2DResource();
```

## <a name="cd2dresourcecd2dresource"></a><a name="cd2dresource"></a>CD2D 资源：CD2D 资源

构造 CD2D 资源对象。

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>参数

*p 父目标*<br/>
指向渲染目标的指针。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

## <a name="cd2dresourcecreate"></a><a name="create"></a>CD2D 资源：创建

创建 CD2D 资源。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>参数

*pRender目标*<br/>
指向渲染目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dresourcedestroy"></a><a name="destroy"></a>CD2D资源：:D

销毁 CD2D 资源对象。

```
virtual void Destroy() = 0;
```

## <a name="cd2dresourceisautodestroy"></a><a name="isautodestroy"></a>CD2D 资源：：自动销毁

检查自动销毁标志。

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>返回值

如果对象将被其所有者销毁，则为 TRUE;否则 FALSE。

## <a name="cd2dresourceisvalid"></a><a name="isvalid"></a>CD2D 资源：有效

检查资源有效性

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>返回值

如果资源有效，则为 TRUE;否则 FALSE。

## <a name="cd2dresourcem_bisautodestroy"></a><a name="m_bisautodestroy"></a>CD2D 资源：m_bIsAutoDestroy

资源将被所有者销毁 （CRenderTarget）

```
BOOL m_bIsAutoDestroy;
```

## <a name="cd2dresourcem_pparenttarget"></a><a name="m_pparenttarget"></a>CD2D 资源：m_pParentTarget

指向父 CRenderTarget 的指针）

```
CRenderTarget* m_pParentTarget;
```

## <a name="cd2dresourcerecreate"></a><a name="recreate"></a>CD2D 资源：重新创建

重新创建 CD2D 资源。

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRender目标*<br/>
指向渲染目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
