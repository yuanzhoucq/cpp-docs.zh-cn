---
title: CDocObjectServerItem 类
ms.date: 03/27/2019
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnDoVerb
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnDoVerb
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
ms.openlocfilehash: 4d44791415626f1a94500b9c3885581d67e8fe42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506824"
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem 类

实现特别针对 DocObject 服务器的 OLE 服务器谓词。

## <a name="syntax"></a>语法

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|name|描述|
|----------|-----------------|
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|构造 `CDocObjectServerItem` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDocObjectServerItem::GetDocument](#getdocument)|检索指向包含该项的文档的指针。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CDocObjectServerItem::OnDoVerb](#ondoverb)|调用以执行谓词。|
|[CDocObjectServerItem::OnHide](#onhide)|如果框架尝试隐藏 DocObject 项, 将引发异常。|
|[CDocObjectServerItem::OnShow](#onshow)|由框架调用以使 DocObject 项处于就地活动状态。 如果项不是 DocObject, 则调用[COleServerItem:: OnShow](../../mfc/reference/coleserveritem-class.md#onshow)。|

## <a name="remarks"></a>备注

`CDocObjectServerItem`定义可重写成员函数:[OnHide](#onhide)、 [OnDoVerb](#ondoverb)和[OnShow](#onshow)。

若要`CDocObjectServerItem`使用, 请确保派生类中`COleServerDoc`的[OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)重写返回一个新`CDocObjectServerItem`的对象。 如果需要更改项中的任何功能, 则可以创建自己`CDocObjectServerItem`的派生类的新实例。

有关 DocObjects 的详细信息, 请参阅*MFC 参考*中的[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[COleCmdUI](../../mfc/reference/colecmdui-class.md) 。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>要求

**标头:** afxdocob

##  <a name="cdocobjectserveritem"></a>CDocObjectServerItem:: CDocObjectServerItem

构造 `CDocObjectServerItem` 对象。

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>参数

*pServerDoc*<br/>
指向将包含新 DocObject 项的文档的指针。

*bAutoDelete*<br/>
指示在释放对象的链接时是否可将其删除。 如果`CDocObjectServerItem`对象是文档数据的组成部分, 则将参数设置为 FALSE。 如果对象是一个辅助结构, 则将其设置为 TRUE, 该结构用于标识可由框架删除的文档数据中的范围。

##  <a name="getdocument"></a>CDocObjectServerItem:: GetDocument

检索指向包含该项的文档的指针。

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>返回值

指向包含该项的文档的指针;如果项不是文档的一部分, 则为 NULL。

### <a name="remarks"></a>备注

这允许访问作为参数传递给[CDocObjectServerItem](#cdocobjectserveritem)构造函数的服务器文档。

##  <a name="ondoverb"></a>  CDocObjectServerItem::OnDoVerb

由框架调用以执行指定的谓词。

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
指定要执行的谓词。 有关可能的值, 请参阅 IOleObject: Windows SDK 中的[::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 。

### <a name="remarks"></a>备注

如果项是 DocObject 并且指定了 OLEIVERB_INPLACEACTIVATE 或 OLEIVERB_SHOW, 则默认实现将调用[OnShow](#onshow)成员函数。 如果项不是 DocObject 或指定了其他谓词, 则默认实现将调用[COleServerItem:: OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb)。

##  <a name="onhide"></a>CDocObjectServerItem:: OnHide

由框架调用以隐藏该项。

```
virtual void OnHide();
```

### <a name="remarks"></a>备注

如果项是 DocObject, 则默认实现会引发异常。 不能隐藏活动的 DocObject 项, 因为它将使用整个视图。 必须停用 DocObject 项以使其消失。 如果项不是 DocObject, 则默认实现将调用[COleServerItem:: OnHide](../../mfc/reference/coleserveritem-class.md#onhide)。

##  <a name="onshow"></a>CDocObjectServerItem:: OnShow

由框架调用, 指示服务器应用程序将 DocObject 项设置为就地活动。

```
virtual void OnShow();
```

### <a name="remarks"></a>备注

如果项不是 DocObject, 则默认实现将调用[COleServerItem:: OnShow](../../mfc/reference/coleserveritem-class.md#onopen)。 如果希望在打开 DocObject 项时执行特殊处理, 请重写此函数。

## <a name="see-also"></a>请参阅

[COleServerItem 类](../../mfc/reference/coleserveritem-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer 类](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem 类](../../mfc/reference/coledocobjectitem-class.md)
