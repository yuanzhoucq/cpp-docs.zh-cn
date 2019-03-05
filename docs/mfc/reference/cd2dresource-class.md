---
title: CD2DResource 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 04d1fa57e34528f96f505fa20abb9b1131f80689
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284861"
---
# <a name="cd2dresource-class"></a>CD2DResource 类

提供用于创建和管理如画笔、 层和文本的 D2D 资源的界面一个抽象类。

## <a name="syntax"></a>语法

```
class CD2DResource : public CObject;
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CD2DResource::CD2DResource](#cd2dresource)|构造一个 CD2DResource 对象。|
|[CD2DResource::~CD2DResource](#cd2dresource__~cd2dresource)|析构函数。 当 D2D 资源对象被销毁时调用。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CD2DResource::Create](#create)|创建 CD2DResource。|
|[CD2DResource::Destroy](#destroy)|销毁 CD2DResource 对象。|
|[CD2DResource::IsValid](#isvalid)|检查资源有效性|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CD2DResource::IsAutoDestroy](#isautodestroy)|检查自动销毁标志。|
|[CD2DResource::ReCreate](#recreate)|重新创建 CD2DResource。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CD2DResource::m_bIsAutoDestroy](#m_bisautodestroy)|资源将是由所有者 (CRenderTarget) destoyed|
|[CD2DResource::m_pParentTarget](#m_pparenttarget)|指向父 CRenderTarget）|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CD2DResource`

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="_dtorcd2dresource"></a>  CD2DResource:: ~ CD2DResource

析构函数。 当 D2D 资源对象被销毁时调用。

```
virtual ~CD2DResource();
```

##  <a name="cd2dresource"></a>  CD2DResource::CD2DResource

构造一个 CD2DResource 对象。

```
CD2DResource(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy);
```

### <a name="parameters"></a>参数

*pParentTarget*<br/>
指向该呈现器目标的指针。

*bAutoDestroy*<br/>
指示所有者 (pParentTarget) 将销毁该对象。

##  <a name="create"></a>  CD2DResource::Create

创建 CD2DResource。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget) = 0;
```

### <a name="parameters"></a>参数

*pRenderTarget*<br/>
指向该呈现器目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。

##  <a name="destroy"></a>  CD2DResource::Destroy

销毁 CD2DResource 对象。

```
virtual void Destroy() = 0;
```

##  <a name="isautodestroy"></a>  CD2DResource::IsAutoDestroy

检查自动销毁标志。

```
BOOL IsAutoDestroy() const;
```

### <a name="return-value"></a>返回值

如果该对象将销毁由其所有者; 则为 TRUE否则为 FALSE。

##  <a name="isvalid"></a>  CD2DResource::IsValid

检查资源有效性

```
virtual BOOL IsValid() const = 0;
```

### <a name="return-value"></a>返回值

如果资源是有效，则为，TRUE否则为 FALSE。

##  <a name="m_bisautodestroy"></a>  CD2DResource::m_bIsAutoDestroy

资源将是由所有者 (CRenderTarget) destoyed

```
BOOL m_bIsAutoDestroy;
```

##  <a name="m_pparenttarget"></a>  CD2DResource::m_pParentTarget

指向父 CRenderTarget）

```
CRenderTarget* m_pParentTarget;
```

##  <a name="recreate"></a>  CD2DResource::ReCreate

重新创建 CD2DResource。

```
virtual HRESULT ReCreate(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRenderTarget*<br/>
指向该呈现器目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
