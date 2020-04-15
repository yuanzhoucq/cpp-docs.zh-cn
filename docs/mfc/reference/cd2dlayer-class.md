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
ms.openlocfilehash: aa6fb313bfcc2983f167936e5ad4f78be1e17a44
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369213"
---
# <a name="cd2dlayer-class"></a>CD2DLayer 类

ID2D1Layer 的包装器。

## <a name="syntax"></a>语法

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2DLayer：CD2DLayer](#cd2dlayer)|构造 CD2DLayer 对象。|
|[CD2DLayer：*CD2DLayer](#_dtorcd2dlayer)|析构函数。 销毁 D2D 图层对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2DLayer：附加](#attach)|将现有资源接口附加到对象|
|[CD2DLayer：创建](#create)|创建 CD2DLayer。 （覆盖[CD2D 资源：创建](../../mfc/reference/cd2dresource-class.md#create).）|
|[CD2DLayer：:D](#destroy)|销毁 CD2DLayer 对象。 （覆盖[CD2D 资源：:D）](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2DLayer：:D](#detach)|从对象分离资源接口|
|[CD2DLayer：获取](#get)|返回 ID2D1Layer 接口|
|[CD2DLayer：获取 Size](#getsize)|返回与设备无关的像素的渲染目标的大小|
|[CD2DLayer：有效](#isvalid)|检查资源有效性（覆盖[CD2D 资源：：有效](../../mfc/reference/cd2dresource-class.md#isvalid)。）|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2DLayer：：操作员 ID2D1Layer*](#operator_id2d1layer_star)|返回 ID2D1Layer 接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2DLayer：m_pLayer](#m_player)|存储指向 ID2D1Layer 对象的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dlayercd2dlayer"></a><a name="_dtorcd2dlayer"></a>CD2DLayer：*CD2DLayer

析构函数。 销毁 D2D 图层对象时调用。

```
virtual ~CD2DLayer();
```

## <a name="cd2dlayerattach"></a><a name="attach"></a>CD2DLayer：附加

将现有资源接口附加到对象

```
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>参数

*p资源*<br/>
现有资源接口。 不能为 NULL

## <a name="cd2dlayercd2dlayer"></a><a name="cd2dlayer"></a>CD2DLayer：CD2DLayer

构造 CD2DLayer 对象。

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*p 父目标*<br/>
指向渲染目标的指针。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

## <a name="cd2dlayercreate"></a><a name="create"></a>CD2DLayer：创建

创建 CD2DLayer。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRender目标*<br/>
指向渲染目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dlayerdestroy"></a><a name="destroy"></a>CD2DLayer：:D

销毁 CD2DLayer 对象。

```
virtual void Destroy();
```

## <a name="cd2dlayerdetach"></a><a name="detach"></a>CD2DLayer：:D

从对象分离资源接口

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>返回值

指向分离的资源接口的指针。

## <a name="cd2dlayerget"></a><a name="get"></a>CD2DLayer：获取

返回 ID2D1Layer 接口

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1Layer 接口或 NULL 的指针。

## <a name="cd2dlayergetsize"></a><a name="getsize"></a>CD2DLayer：获取 Size

返回与设备无关的像素的渲染目标的大小

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>返回值

以与设备无关的像素表示渲染目标的当前大小

## <a name="cd2dlayerisvalid"></a><a name="isvalid"></a>CD2DLayer：有效

检查资源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源有效，则为 TRUE;否则 FALSE。

## <a name="cd2dlayerm_player"></a><a name="m_player"></a>CD2DLayer：m_pLayer

存储指向 ID2D1Layer 对象的指针。

```
ID2D1Layer* m_pLayer;
```

## <a name="cd2dlayeroperator-id2d1layer"></a><a name="operator_id2d1layer_star"></a>CD2DLayer：：操作员 ID2D1Layer*

返回 ID2D1Layer 接口

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1Layer 接口或 NULL 的指针。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
