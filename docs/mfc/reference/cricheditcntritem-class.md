---
title: CRichEditCntrItem 类
ms.date: 11/04/2016
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
ms.openlocfilehash: 674937df9b4ecef0d159a47a45a716d1175ad5d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372109"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem 类

与[CRichEditView](../../mfc/reference/cricheditview-class.md)并[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，提供 MFC 文档视图体系结构的上下文中 rich edit 控件的功能。

## <a name="syntax"></a>语法

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|构造 `CRichEditCntrItem` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|作为另一种类型将激活该项。|

## <a name="remarks"></a>备注

"格式文本编辑控件"是一个窗口，用户可以输入和编辑文本。 文本字符和段落格式设置，可以分配，并且可以包含嵌入的 OLE 对象。 Rich edit 控件提供用于设置文本格式的编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。

`CRichEditView` 保留文本及其格式特征。 `CRichEditDoc` 维护视图中的 OLE 客户端项目的列表。 `CRichEditCntrItem` 提供对 OLE 客户端项的容器端访问。

此 Windows 公共控件 (并因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相关类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。

在 MFC 应用程序中使用格式文本编辑容器项的示例，请参阅[写字板](../../overview/visual-cpp-samples.md)示例应用程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>要求

**标头：** afxrich.h

##  <a name="cricheditcntritem"></a>  CRichEditCntrItem::CRichEditCntrItem

调用此函数可创建`CRichEditCntrItem`对象，并将其添加到容器文档。

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>参数

*preo*<br/>
指向[REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject)结构描述 OLE 项。 新`CRichEditCntrItem`此 OLE 项的周围构造对象。 如果*preo*为 NULL，客户端项为空。

*pContainer*<br/>
指向将包含此项的容器文档的指针。 如果*pContainer*为 NULL，必须显式调用[COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem)若要将此客户端项目添加到文档。

### <a name="remarks"></a>备注

此函数不执行任何 OLE 初始化。

有关详细信息，请参阅[REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) Windows SDK 中的结构。

##  <a name="synctoricheditobject"></a>  CRichEditCntrItem::SyncToRichEditObject

调用此函数可同步设备方面[DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect)，此`CRichEditCntrltem`到指定的*reo*。

```
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>参数

*reo*<br/>
引用[REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject)结构描述 OLE 项。

### <a name="remarks"></a>备注

有关详细信息，请参阅[DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) Windows SDK 中。

## <a name="see-also"></a>请参阅

[MFC 示例写字板](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 类](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView 类](../../mfc/reference/cricheditview-class.md)
