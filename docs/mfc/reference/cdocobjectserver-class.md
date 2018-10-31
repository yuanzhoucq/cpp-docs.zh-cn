---
title: CDocObjectServer 类 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
dev_langs:
- C++
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 552252c8826e167b4aaa21aa41e489bbc8179ec3
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890370"
---
# <a name="cdocobjectserver-class"></a>CDocObjectServer 类

实现将常规 `COleDocument` 服务器接入完整 DocObject 服务器所需的其他 OLE 接口： `IOleDocument`、 `IOleDocumentView`、 `IOleCommandTarget`和 `IPrint`。

## <a name="syntax"></a>语法

```
class CDocObjectServer : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|构造 `CDocObjectServer` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|激活文档对象服务器，但不显示它。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CDocObjectServer::OnActivateView](#onactivateview)|显示 DocObject 视图。|
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|还原 DocObject 视图的状态。|
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|保存 DocObject 视图的状态。|

## <a name="remarks"></a>备注

`CDocObjectServer` 派生自`CCmdTarget`紧密配合`COleServerDoc`公开的接口。

DocObject 服务器文档可以包含[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) DocObject 项代表服务器接口的对象。

若要自定义 DocObject 服务器，派生您自己的类从`CDocObjectServer`并重写其查看安装程序函数， [OnActivateView](#onactivateview)， [OnApplyViewState](#onapplyviewstate)，并[OnSaveViewState](#onsaveviewstate). 需要提供你到框架将调用的响应中的类的新实例。

DocObjects 的详细信息，请参阅[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)并[COleCmdUI](../../mfc/reference/colecmdui-class.md)中*MFC 参考*。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>要求

**标头：** afxdocob.h

##  <a name="activatedocobject"></a>  CDocObjectServer::ActivateDocObject

调用此函数可激活 （但不是显示） 文档对象服务器。

```
void ActivateDocObject();
```

### <a name="remarks"></a>备注

`ActivateDocObject` 调用`IOleDocumentSite`的`ActivateMe`方法，但不显示该视图，因为它在等待如何设置并显示在视图中，对的调用中给定的具体说明[CDocObjectServer::OnActivateView](#onactivateview)。

共同`ActivateDocObject`和`OnActivateView`激活并显示 DocObject 视图。 DocObject 激活不同于其他类型的 OLE 就地激活。 DocObject 激活会绕过显示就地阴影边框和对象 （如大小调整控点） 的修饰，忽略对象扩展盘区功能，并绘制滚动条，而不是外部 （如中所示正常该矩形中绘制它们的视图矩形中就地激活）。

##  <a name="cdocobjectserver"></a>  CDocObjectServer::CDocObjectServer

构造并初始化一个 `CDocObjectServer` 对象。

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>参数

*pOwner*<br/>
指向 DocObject 服务器的客户端的客户端站点文档的指针。

*pDocSite*<br/>
一个指向`IOleDocumentSite`由容器实现的接口。

### <a name="remarks"></a>备注

当 DocObject 处于活动状态时，客户端站点 OLE 接口 ( `IOleDocumentSite`) 是什么使 DocObject 服务器与它的客户端 （容器） 进行通信。 激活 DocObject 服务器时，它首先检查该容器实现`IOleDocumentSite`接口。 如果是这样， [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver)称为容器是否支持 DocObjects。 默认情况下，`GetDocObjectServer`返回 NULL。 必须重写`COleServerDoc::GetDocObjectServer`来构造一个新`CDocObjectServer`对象或你自己，具有指向派生的对象`COleServerDoc`容器并将其`IOleDocumentSite`接口作为构造函数的参数。

##  <a name="onactivateview"></a>  CDocObjectServer::OnActivateView

调用此函数可显示 DocObject 视图。

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>返回值

返回的错误或警告值。 默认情况下，将返回 NOERROR 如果成功，则否则为 E_FAIL。

### <a name="remarks"></a>备注

此函数创建就地框架窗口、 绘制在视图中的滚动条、 设置服务器与它的容器共享、 添加框架控件、 设置活动的对象，然后最后显示的就地框架窗口，并将焦点设置的菜单。

##  <a name="onapplyviewstate"></a>  CDocObjectServer::OnApplyViewState

重写此函数可还原 DocObject 视图的状态。

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
一个`CArchive`从中序列化的视图状态对象。

### <a name="remarks"></a>备注

视图在其实例化后第一次显示时调用此函数。 `OnApplyViewState` 指示要重新初始化自身根据中的数据的视图`CArchive`对象以前保存的与[OnSaveViewState](#onsaveviewstate)。 视图必须验证中的数据`CArchive`对象，因为该容器不会尝试解释以任何方式的视图状态数据。

可以使用`OnSaveViewState`来存储特定于您的视图状态持久性信息。 如果重写`OnSaveViewState`来存储信息，将想要重写`OnApplyViewState`读取该信息并将其应用到视图中，新激活时。

##  <a name="onsaveviewstate"></a>  CDocObjectServer::OnSaveViewState

重写此函数可保存 DocObject 视图有关的额外状态信息。

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
一个`CArchive`的视图状态序列化到对象。

### <a name="remarks"></a>备注

你的状态可能包含属性，如视图类型、 缩放系数、 插入和选择点等。 容器通常会在停用视图之前调用此函数。 更高版本可以通过还原的已保存的状态[OnApplyViewState](#onapplyviewstate)。

可以使用`OnSaveViewState`来存储特定于您的视图状态持久性信息。 如果重写`OnSaveViewState`来存储信息，将想要重写`OnApplyViewState`读取该信息并将其应用到视图中，新激活时。

## <a name="see-also"></a>请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServerItem 类](../../mfc/reference/cdocobjectserveritem-class.md)
