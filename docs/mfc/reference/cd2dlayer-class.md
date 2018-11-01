---
title: CD2DLayer 类
ms.date: 11/04/2016
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
ms.openlocfilehash: cd4452eeb9e600aeabaec1b54fd40217514e02eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531711"
---
# <a name="cd2dlayer-class"></a>CD2DLayer 类

ID2D1Layer 包装器。

## <a name="syntax"></a>语法

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DLayer::CD2DLayer](#cd2dlayer)|构造一个 CD2DLayer 对象。|
|[CD2DLayer:: ~ CD2DLayer](#_dtorcd2dlayer)|析构函数。 当 D2D 层对象被销毁时调用。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CD2DLayer::Attach](#attach)|附加现有的资源的对象的接口|
|[CD2DLayer::Create](#create)|创建 CD2DLayer。 (重写[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|
|[CD2DLayer::Destroy](#destroy)|销毁 CD2DLayer 对象。 (重写[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|
|[CD2DLayer::Detach](#detach)|分离对象中的资源接口|
|[CD2DLayer::Get](#get)|返回 ID2D1Layer 接口|
|[CD2DLayer::GetSize](#getsize)|以独立于设备的像素为单位返回呈现器目标的大小|
|[CD2DLayer::IsValid](#isvalid)|检查资源有效性 (重写[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CD2DLayer::operator ID2D1Layer *](#operator_id2d1layer_star)|返回 ID2D1Layer 接口|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CD2DLayer::m_pLayer](#m_player)|存储指向 ID2D1Layer 对象的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="_dtorcd2dlayer"></a>  CD2DLayer:: ~ CD2DLayer

析构函数。 当 D2D 层对象被销毁时调用。

```
virtual ~CD2DLayer();
```

##  <a name="attach"></a>  CD2DLayer::Attach

附加现有的资源的对象的接口

```
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>参数

*pResource*<br/>
现有资源的接口。 不能为 NULL

##  <a name="cd2dlayer"></a>  CD2DLayer::CD2DLayer

构造一个 CD2DLayer 对象。

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*pParentTarget*<br/>
指向该呈现器目标的指针。

*bAutoDestroy*<br/>
指示所有者 (pParentTarget) 将销毁该对象。

##  <a name="create"></a>  CD2DLayer::Create

创建 CD2DLayer。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRenderTarget*<br/>
指向该呈现器目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。

##  <a name="destroy"></a>  CD2DLayer::Destroy

销毁 CD2DLayer 对象。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DLayer::Detach

分离对象中的资源接口

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>返回值

指向已分离的资源接口指针。

##  <a name="get"></a>  CD2DLayer::Get

返回 ID2D1Layer 接口

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>返回值

指向 ID2D1Layer 接口或如果对象尚未初始化，则为 NULL 指针。

##  <a name="getsize"></a>  CD2DLayer::GetSize

以独立于设备的像素为单位返回呈现器目标的大小

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>返回值

以独立于设备的像素为单位的呈现器目标的当前大小

##  <a name="isvalid"></a>  CD2DLayer::IsValid

检查资源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源是有效，则为，TRUE否则为 FALSE。

##  <a name="m_player"></a>  CD2DLayer::m_pLayer

存储指向 ID2D1Layer 对象的指针。

```
ID2D1Layer* m_pLayer;
```

##  <a name="operator_id2d1layer_star"></a>  CD2DLayer::operator ID2D1Layer *

返回 ID2D1Layer 接口

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>返回值

指向 ID2D1Layer 接口或如果对象尚未初始化，则为 NULL 指针。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
