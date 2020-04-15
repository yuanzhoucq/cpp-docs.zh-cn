---
title: CDocObjectServer 项目类
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
ms.openlocfilehash: 1f0f5cf93aab35a17f7174b2beee0d1398564a3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375529"
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServer 项目类

实现特别针对 DocObject 服务器的 OLE 服务器谓词。

## <a name="syntax"></a>语法

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CDocObjectServer项目：CDocObjectServer项目](#cdocobjectserveritem)|构造 `CDocObjectServerItem` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDocObjectServer项目：获取文档](#getdocument)|检索指向包含项的文档的指针。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CDocObjectServer项目：：OnDoVerb](#ondoverb)|被调用以执行动词。|
|[CDocObjectServer项目：：打开隐藏](#onhide)|如果框架尝试隐藏 DocObject 项，则引发异常。|
|[CDocObjectServer项目：：在展会上](#onshow)|由框架调用以使 DocObject 项就地处于活动状态。 如果项目不是 DocObject，请调用[COleServerItem：：onShow。](../../mfc/reference/coleserveritem-class.md#onshow)|

## <a name="remarks"></a>备注

`CDocObjectServerItem`定义可重写的成员函数[：OnHide、OnDoVerb](#onhide)和[OnShow](#onshow)。 [OnDoVerb](#ondoverb)

要使用`CDocObjectServerItem`，`COleServerDoc`确保派生类中的`CDocObjectServerItem`[OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)重写返回一个新对象。 如果需要更改项目中的任何功能，可以创建自己的`CDocObjectServerItem`派生类的新实例。

有关文档对象的详细信息，请参阅*MFC 参考*中的[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[COleCmdUI。](../../mfc/reference/colecmdui-class.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>要求

**标题：** afxdocob.h

## <a name="cdocobjectserveritemcdocobjectserveritem"></a><a name="cdocobjectserveritem"></a>CDocObjectServer项目：CDocObjectServer项目

构造 `CDocObjectServerItem` 对象。

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>参数

*pServerDoc*<br/>
指向将包含新 DocObject 项的文档的指针。

*b自动删除*<br/>
指示在释放指向该对象的链接时是否可以删除该对象。 如果对象是文档数据的组成部分，`CDocObjectServerItem`则将参数设置为 FALSE。 如果对象是用于标识文档数据中可由框架删除的范围的辅助结构，则将其设置为 TRUE。

## <a name="cdocobjectserveritemgetdocument"></a><a name="getdocument"></a>CDocObjectServer项目：获取文档

检索指向包含项的文档的指针。

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>返回值

指向包含项的文档的指针;如果项目不是文档的一部分，则 NULL。

### <a name="remarks"></a>备注

这允许访问作为参数传递给[CDocObjectServerItem](#cdocobjectserveritem)构造函数的服务器文档。

## <a name="cdocobjectserveritemondoverb"></a><a name="ondoverb"></a>CDocObjectServer项目：：OnDoVerb

由框架调用以执行指定的谓词。

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>参数

*iVerb*<br/>
指定要执行的谓词。 有关可能的值，请参阅 Windows SDK 中的[IOleObject：:DoVerb。](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)

### <a name="remarks"></a>备注

如果项目是 DocObject 并指定了OLEIVERB_INPLACEACTIVATE或OLEIVERB_SHOW，则默认实现将调用[OnShow](#onshow)成员函数。 如果项不是 DocObject 或指定了其他谓词，则默认实现将调用[COleServerItem：：OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb)。

## <a name="cdocobjectserveritemonhide"></a><a name="onhide"></a>CDocObjectServer项目：：打开隐藏

由框架调用以隐藏项。

```
virtual void OnHide();
```

### <a name="remarks"></a>备注

如果项是 DocObject，则默认实现将引发异常。 不能隐藏活动文档对象项，因为它占用整个视图。 您必须停用 DocObject 项才能将其消失。 如果项目不是 DocObject，则默认实现将调用[COleServerItem：：onHide。](../../mfc/reference/coleserveritem-class.md#onhide)

## <a name="cdocobjectserveritemonshow"></a><a name="onshow"></a>CDocObjectServer项目：：在展会上

由框架调用，指示服务器应用程序使 DocObject 项就地处于活动状态。

```
virtual void OnShow();
```

### <a name="remarks"></a>备注

如果项目不是 DocObject，则默认实现将调用[COleServerItem：：onShow。](../../mfc/reference/coleserveritem-class.md#onopen) 如果要在打开 DocObject 项时执行特殊处理，则重写此函数。

## <a name="see-also"></a>另请参阅

[COleServer 项目类](../../mfc/reference/coleserveritem-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer 类](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem 类](../../mfc/reference/coledocobjectitem-class.md)
