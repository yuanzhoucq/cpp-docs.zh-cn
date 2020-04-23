---
title: CDocObjectServer 类
ms.date: 09/12/2018
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
ms.openlocfilehash: f415df35b13e50eee092f87eca0627e5cf143720
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753292"
---
# <a name="cdocobjectserver-class"></a>CDocObjectServer 类

实现将常规 `COleDocument` 服务器接入完整 DocObject 服务器所需的其他 OLE 接口： `IOleDocument`、 `IOleDocumentView`、 `IOleCommandTarget`和 `IPrint`。

## <a name="syntax"></a>语法

```
class CDocObjectServer : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDocObject服务器：CDocObjectServer](#cdocobjectserver)|构造 `CDocObjectServer` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDocObject 服务器：激活文档对象](#activatedocobject)|激活文档对象服务器，但不显示它。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CDocObject服务器：打开激活视图](#onactivateview)|显示文档对象视图。|
|[CDocObject服务器：在应用视图状态](#onapplyviewstate)|还原文档对象视图的状态。|
|[CDocObject服务器：：在保存视图状态](#onsaveviewstate)|保存文档对象视图的状态。|

## <a name="remarks"></a>备注

`CDocObjectServer`派生自`CCmdTarget`并紧密地与`COleServerDoc`公开接口。

DocObject 服务器文档可以包含[CDocObjectServerItem 对象](../../mfc/reference/cdocobjectserveritem-class.md)，这些对象表示文档对象项的服务器接口。

要自定义文档对象服务器，`CDocObjectServer`请从其视图设置功能["启用"、应用](#onactivateview)[视图](#onapplyviewstate)状态和[OnSaveViewState](#onsaveviewstate)派生您自己的类并重写其视图设置功能。 您需要提供类的新实例来响应框架调用。

有关文档对象的详细信息，请参阅*MFC 参考*中的[CDocObjectServerItem 项目和](../../mfc/reference/cdocobjectserveritem-class.md) [COleCmdUI。](../../mfc/reference/colecmdui-class.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>要求

**标题：** afxdocob.h

## <a name="cdocobjectserveractivatedocobject"></a><a name="activatedocobject"></a>CDocObject 服务器：激活文档对象

调用此函数以激活（但不显示）文档对象服务器。

```cpp
void ActivateDocObject();
```

### <a name="remarks"></a>备注

`ActivateDocObject`调用`IOleDocumentSite`的方法`ActivateMe`，但不显示视图，因为它等待有关如何设置和显示视图的特定说明，在调用[CDocObjectServer 时给出：：OnActivateView](#onactivateview)。

一起`ActivateDocObject`，`OnActivateView`并激活和显示文档对象视图。 DocObject 激活不同于其他类型的 OLE 就地激活。 DocObject 激活绕过显示就地填充边框和对象修饰（如大小调整控点），忽略对象范围函数，并在视图矩形中绘制滚动条，而不是将其绘制到该矩形之外（如正常就地激活）。

## <a name="cdocobjectservercdocobjectserver"></a><a name="cdocobjectserver"></a>CDocObject服务器：CDocObjectServer

构造并初始化一个 `CDocObjectServer` 对象。

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>参数

*pOwner*<br/>
指向客户端站点文档的指针，该文档是 DocObject 服务器的客户端。

*pDocSite*<br/>
指向容器实现的`IOleDocumentSite`接口的指针。

### <a name="remarks"></a>备注

当 DocObject 处于活动状态时，客户端站点 OLE`IOleDocumentSite`接口 （ ） 是允许 DocObject 服务器与其客户端（容器）通信的原因。 激活 DocObject 服务器时，它首先检查容器是否实现了`IOleDocumentSite`接口。 如果是这样，则调用[COleServerDoc：getDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver)以查看容器是否支持文档对象。 默认情况下，`GetDocObjectServer`返回 NULL。 必须重写`COleServerDoc::GetDocObjectServer`以构造自己的新`CDocObjectServer`对象或派生对象，并将指向`COleServerDoc`容器及其`IOleDocumentSite`接口的指针作为构造函数的参数。

## <a name="cdocobjectserveronactivateview"></a><a name="onactivateview"></a>CDocObject服务器：打开激活视图

调用此函数以显示文档对象视图。

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>返回值

返回错误或警告值。 默认情况下，如果成功，则返回 NOERROR;否则，E_FAIL。

### <a name="remarks"></a>备注

此函数创建一个就地框架窗口，在视图中绘制滚动条，设置服务器与其容器共享的菜单，添加帧控件，设置活动对象，最后显示就地框架窗口并设置焦点。

## <a name="cdocobjectserveronapplyviewstate"></a><a name="onapplyviewstate"></a>CDocObject服务器：在应用视图状态

重写此函数以还原文档对象视图的状态。

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
用于`CArchive`序列化视图状态的对象。

### <a name="remarks"></a>备注

当视图在实例化后首次显示时，将调用此功能。 `OnApplyViewState`指示视图根据以前与[OnSaveViewState](#onsaveviewstate)一起保存的对象`CArchive`中的数据重新初始化自身。 视图必须验证对象中`CArchive`的数据，因为容器不会尝试以任何方式解释视图状态数据。

可以使用`OnSaveViewState`来存储特定于视图状态的持久信息。 如果重写`OnSaveViewState`以存储信息，则需要重写`OnApplyViewState`以读取该信息，并在视图新激活时将其应用于视图。

## <a name="cdocobjectserveronsaveviewstate"></a><a name="onsaveviewstate"></a>CDocObject服务器：：在保存视图状态

重写此函数以保存有关 DocObject 视图的额外状态信息。

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
视图`CArchive`状态序列化的对象。

### <a name="remarks"></a>备注

您的状态可能包括视图类型、缩放系数、插入和选择点等属性。 容器通常在停用视图之前调用此函数。 保存的状态稍后可以通过[OnApplyViewState](#onapplyviewstate)还原。

可以使用`OnSaveViewState`来存储特定于视图状态的持久信息。 如果重写`OnSaveViewState`以存储信息，则需要重写`OnApplyViewState`以读取该信息，并在视图新激活时将其应用于视图。

## <a name="see-also"></a>请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer 项目类](../../mfc/reference/cdocobjectserveritem-class.md)
