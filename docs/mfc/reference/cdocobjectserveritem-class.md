---
title: CDocObjectServerItem 类
ms.date: 09/12/2018
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
ms.openlocfilehash: cecbab366b64c85b39131a13233598abec83d5ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536521"
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem 类

实现特别针对 DocObject 服务器的 OLE 服务器谓词。

## <a name="syntax"></a>语法

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|构造 `CDocObjectServerItem` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDocObjectServerItem::GetDocument](#getdocument)|检索指向包含项的文档。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CDocObjectServerItem::OnDoVerb](#ondoverb)|如果框架试图隐藏 DocObject 项，将引发异常。|
|[CDocObjectServerItem::OnHide](#onhide)|如果框架试图隐藏 DocObject 项，将引发异常。|
|[CDocObjectServerItem::OnShow](#onshow)|由框架调用以使该文档项就地活动状态。 如果项不是 DocObject，调用[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow)。|

## <a name="remarks"></a>备注

`CDocObjectServerItem` 定义可重写成员函数： [OnHide](#onhide)， [OnDoVerb](#ondoverb)，并[OnShow](#onshow)。

若要使用`CDocObjectServerItem`，确保[OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)重写中你`COleServerDoc`-派生的类返回一个新`CDocObjectServerItem`对象。 如果需要更改你的项中的任何功能，可以创建自己的新实例`CDocObjectServerItem`-派生的类。

DocObjects 的详细信息，请参阅[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)并[COleCmdUI](../../mfc/reference/colecmdui-class.md)中*MFC 参考*。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>要求

**标头：** afxdocob.h

##  <a name="cdocobjectserveritem"></a>  CDocObjectServerItem::CDocObjectServerItem

构造 `CDocObjectServerItem` 对象。

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>参数

*pServerDoc*<br/>
指向将包含新 DocObject 项的文档的指针。

*bAutoDelete*<br/>
指示链接到该发布时是否可以删除该对象。 将参数设置为 FALSE;`CDocObjectServerItem`对象是不可或缺的一部分文档的数据。 将其设置为 TRUE 的对象是否用于标识可以通过该框架来删除文档的数据中的范围的辅助结构。

##  <a name="getdocument"></a>  CDocObjectServerItem::GetDocument

检索指向包含项的文档。

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>返回值

指向包含的项; 文档如果项不是文档的一部分，则为 NULL。

### <a name="remarks"></a>备注

这样，作为参数传递服务器文档的访问权限[CDocObjectServerItem](#cdocobjectserveritem)构造函数。

##  <a name="onhide"></a>  CDocObjectServerItem::OnHide

由框架调用以隐藏项。

```
virtual void OnHide();
```

### <a name="remarks"></a>备注

如果该项是 DocObject 的默认实现将引发异常。 整个视图，因此，不能隐藏 active DocObject 项。 必须先停用 DocObject 项目，使其消失。 如果项不是 DocObject 的默认实现调用[COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide)。

##  <a name="onshow"></a>  CDocObjectServerItem::OnShow

由框架调用以指示服务器应用程序，以使该文档项就地活动状态。

```
virtual void OnShow();
```

### <a name="remarks"></a>备注

如果项不是 DocObject 的默认实现调用[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen)。 如果你想要执行的特殊处理打开 DocObject 项时，重写此函数。

## <a name="see-also"></a>请参阅

[COleServerItem 类](../../mfc/reference/coleserveritem-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer 类](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem 类](../../mfc/reference/coledocobjectitem-class.md)
