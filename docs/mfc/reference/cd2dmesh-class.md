---
title: CD2DMesh 类
ms.date: 11/04/2016
f1_keywords:
- CD2DMesh
- AFXRENDERTARGET/CD2DMesh
- AFXRENDERTARGET/CD2DMesh::CD2DMesh
- AFXRENDERTARGET/CD2DMesh::Attach
- AFXRENDERTARGET/CD2DMesh::Create
- AFXRENDERTARGET/CD2DMesh::Destroy
- AFXRENDERTARGET/CD2DMesh::Detach
- AFXRENDERTARGET/CD2DMesh::Get
- AFXRENDERTARGET/CD2DMesh::IsValid
- AFXRENDERTARGET/CD2DMesh::Open
- AFXRENDERTARGET/CD2DMesh::m_pMesh
helpviewer_keywords:
- CD2DMesh [MFC], CD2DMesh
- CD2DMesh [MFC], Attach
- CD2DMesh [MFC], Create
- CD2DMesh [MFC], Destroy
- CD2DMesh [MFC], Detach
- CD2DMesh [MFC], Get
- CD2DMesh [MFC], IsValid
- CD2DMesh [MFC], Open
- CD2DMesh [MFC], m_pMesh
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
ms.openlocfilehash: eaecdb6ba6f1382f16177e0567b31c9fd09da6ff
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753093"
---
# <a name="cd2dmesh-class"></a>CD2DMesh 类

ID2D1Mesh 的包装器。

## <a name="syntax"></a>语法

```
class CD2DMesh : public CD2DResource;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2D网格：CD2D网格](#cd2dmesh)|构造 CD2DMesh 对象。|
|[CD2D网格：*CD2D网格](#_dtorcd2dmesh)|析构函数。 销毁 D2D 网格对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CD2D 网格：附加](#attach)|将现有资源接口附加到对象|
|[CD2D 网格：：创建](#create)|创建 CD2D 网格。 （覆盖[CD2D 资源：创建](../../mfc/reference/cd2dresource-class.md#create).）|
|[CD2DMesh：:D](#destroy)|销毁 CD2DMesh 对象。 （覆盖[CD2D 资源：:D）](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2DMesh：:D埃塔奇](#detach)|从对象分离资源接口|
|[CD2D 网格：获取](#get)|返回 ID2D1Mesh 接口|
|[CD2DMesh：有效](#isvalid)|检查资源有效性（覆盖[CD2D 资源：：有效](../../mfc/reference/cd2dresource-class.md#isvalid)。）|
|[CD2D 网格：：打开](#open)|打开网格以表示总体。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CD2D 网格：：操作员 ID2D1Mesh*](#operator_id2d1mesh_star)|返回 ID2D1Mesh 接口|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CD2DMesh：m_pMesh](#m_pmesh)|指向 ID2D1Mesh 的指针。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 资源](../../mfc/reference/cd2dresource-class.md)

`CD2DMesh`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dmeshcd2dmesh"></a><a name="_dtorcd2dmesh"></a>CD2D网格：*CD2D网格

析构函数。 销毁 D2D 网格对象时调用。

```
virtual ~CD2DMesh();
```

## <a name="cd2dmeshattach"></a><a name="attach"></a>CD2D 网格：附加

将现有资源接口附加到对象

```cpp
void Attach(ID2D1Mesh* pResource);
```

### <a name="parameters"></a>参数

*p资源*<br/>
现有资源接口。 不能为 NULL

## <a name="cd2dmeshcd2dmesh"></a><a name="cd2dmesh"></a>CD2D网格：CD2D网格

构造 CD2DMesh 对象。

```
CD2DMesh(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>参数

*p 父目标*<br/>
指向渲染目标的指针。

*bAuto销毁*<br/>
指示对象将被所有者（pParentTarget）销毁。

## <a name="cd2dmeshcreate"></a><a name="create"></a>CD2D 网格：：创建

创建 CD2D 网格。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>参数

*pRender目标*<br/>
指向渲染目标的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="cd2dmeshdestroy"></a><a name="destroy"></a>CD2DMesh：:D

销毁 CD2DMesh 对象。

```
virtual void Destroy();
```

## <a name="cd2dmeshdetach"></a><a name="detach"></a>CD2DMesh：:D埃塔奇

从对象分离资源接口

```
ID2D1Mesh* Detach();
```

### <a name="return-value"></a>返回值

指向分离的资源接口的指针。

## <a name="cd2dmeshget"></a><a name="get"></a>CD2D 网格：获取

返回 ID2D1Mesh 接口

```
ID2D1Mesh* Get();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1Mesh 接口或 NULL 的指针。

## <a name="cd2dmeshisvalid"></a><a name="isvalid"></a>CD2DMesh：有效

检查资源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果资源有效，则为 TRUE;否则 FALSE。

## <a name="cd2dmeshm_pmesh"></a><a name="m_pmesh"></a>CD2DMesh：m_pMesh

指向 ID2D1Mesh 的指针。

```
ID2D1Mesh* m_pMesh;
```

## <a name="cd2dmeshopen"></a><a name="open"></a>CD2D 网格：：打开

打开网格以表示总体。

```
ID2D1TessellationSink* Open();
```

### <a name="return-value"></a>返回值

指向用于填充网格的 ID2D1Tesssssink 的指针。

## <a name="cd2dmeshoperator-id2d1mesh"></a><a name="operator_id2d1mesh_star"></a>CD2D 网格：：操作员 ID2D1Mesh*

返回 ID2D1Mesh 接口

```
operator ID2D1Mesh*();
```

### <a name="return-value"></a>返回值

如果对象尚未初始化，则指向 ID2D1Mesh 接口或 NULL 的指针。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
