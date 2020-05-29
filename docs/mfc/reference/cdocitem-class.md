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
ms.openlocfilehash: 438bc2a03239946dbfca53d5f2989c731b682ab0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375624"
---
# <a name="cdocitem-class"></a>CDocItem 类

属于文档数据一部分的文档项的基类。

## <a name="syntax"></a>语法

```
class CDocItem : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDocItem：获取文档](#getdocument)|返回包含该项目的文档。|
|[CDocItem：：是空白](#isblank)|确定该项目是否包含任何信息。|

## <a name="remarks"></a>备注

`CDocItem`对象用于表示客户端和服务器文档中的 OLE 项。

有关详细信息，请参阅文章["容器：实现容器](../../mfc/containers-implementing-a-container.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocItem`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="cdocitemgetdocument"></a><a name="getdocument"></a>CDocItem：获取文档

调用此函数以获取包含项的文档。

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>返回值

指向包含项的文档的指针;NULL，如果项不是文档的一部分。

### <a name="remarks"></a>备注

此函数在派生类[COleClientItem](../../mfc/reference/coleclientitem-class.md)和[COleServerItem](../../mfc/reference/coleserveritem-class.md)中重写，返回指向[COleDocument、COle](../../mfc/reference/coledocument-class.md)[链接文档](../../mfc/reference/colelinkingdoc-class.md)或[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)对象的指针。

## <a name="cdocitemisblank"></a><a name="isblank"></a>CDocItem：：是空白

当发生默认序列化时，由框架调用。

```
virtual BOOL IsBlank() const;
```

### <a name="return-value"></a>返回值

如果项目不包含任何信息，则非零;否则 0。

### <a name="remarks"></a>备注

默认情况下，`CDocItem`对象不为空。 [COleClientItem 对象](../../mfc/reference/coleclientitem-class.md)有时为空，因为它们直接派生`CDocItem`自 。 但是[，COleServerItem 对象](../../mfc/reference/coleserveritem-class.md)始终为空。 默认情况下，包含`COleClientItem`没有 x 或 y 范围对象的 OLE 应用程序将序列化。 这是通过从项目没有 x 或`IsBlank`y 范围时从重写返回 TRUE 来实现的。

如果要在序列化期间实现其他操作，则重写此函数。

## <a name="see-also"></a>另请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDocument 类](../../mfc/reference/coledocument-class.md)<br/>
[COleServer 项目类](../../mfc/reference/coleserveritem-class.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)
