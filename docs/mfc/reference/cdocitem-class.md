---
title: CDocItem 类
ms.date: 11/04/2016
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
ms.openlocfilehash: 6c1c1da14d732b6aff6ae07f86ae7b9c1b690b84
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291309"
---
# <a name="cdocitem-class"></a>CDocItem 类

属于文档数据一部分的文档项的基类。

## <a name="syntax"></a>语法

```
class CDocItem : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDocItem::GetDocument](#getdocument)|返回包含项的文档。|
|[CDocItem::IsBlank](#isblank)|确定项是否包含任何信息。|

## <a name="remarks"></a>备注

`CDocItem` 对象用于表示在客户端和服务器文档中的 OLE 项。

有关详细信息，请参阅文章[容器：实现容器](../../mfc/containers-implementing-a-container.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocItem`

## <a name="requirements"></a>要求

**标头：** afxole.h

##  <a name="getdocument"></a>  CDocItem::GetDocument

调用此函数可获取包含该项的文档。

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>返回值

指向包含的项; 文档如果项不是文档的一部分，则为 NULL。

### <a name="remarks"></a>备注

在派生类中重写此函数[COleClientItem](../../mfc/reference/coleclientitem-class.md)并[COleServerItem](../../mfc/reference/coleserveritem-class.md)，为返回的指针[COleDocument](../../mfc/reference/coledocument-class.md)、 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)，或[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)对象。

##  <a name="isblank"></a>  CDocItem::IsBlank

默认的序列化时由框架调用。

```
virtual BOOL IsBlank() const;
```

### <a name="return-value"></a>返回值

非零，如果项不包含任何信息;否则为 0。

### <a name="remarks"></a>备注

默认情况下，`CDocItem`对象是否不为空。 [COleClientItem](../../mfc/reference/coleclientitem-class.md)对象，有时空白因为它们直接派生`CDocItem`。 但是， [COleServerItem](../../mfc/reference/coleserveritem-class.md)对象始终为空白。 默认情况下，包含 OLE 应用程序`COleClientItem`没有 x 或 y 的对象进行序列化程度。 这是通过从的重写返回 TRUE`IsBlank`项时出现没有 x 或 y 扩展盘区。

如果你想要在序列化期间执行其他操作，重写此函数。

## <a name="see-also"></a>请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[COleDocument 类](../../mfc/reference/coledocument-class.md)<br/>
[COleServerItem 类](../../mfc/reference/coleserveritem-class.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)
