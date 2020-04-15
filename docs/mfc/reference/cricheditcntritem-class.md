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
ms.openlocfilehash: b8158105d09d5cfc7c25512567a98121b194a82a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368292"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem 类

使用[CRichEditView](../../mfc/reference/cricheditview-class.md)和[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，在 MFC 的文档视图体系结构的上下文中提供了丰富的编辑控件的功能。

## <a name="syntax"></a>语法

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[克里希编辑项目：：克里希编辑Cntrtr项目](#cricheditcntritem)|构造 `CRichEditCntrItem` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[克里希编辑项目：：同步到里希编辑对象](#synctoricheditobject)|将该项目激活为另一种类型。|

## <a name="remarks"></a>备注

"富编辑控件"是用户可以在其中输入和编辑文本的窗口。 文本可以分配字符和段落格式，并可以包括嵌入的 OLE 对象。 丰富的编辑控件为文本格式设置提供了编程界面。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。

`CRichEditView` 保留文本及其格式特征。 `CRichEditDoc`维护视图中的 OLE 客户端项的列表。 `CRichEditCntrItem` 提供对 OLE 客户端项的容器端访问。

此 Windows 通用控件（因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相关类）仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下运行的程序。

有关在 MFC 应用程序中使用富编辑容器项的示例，请参阅[WORDPAD](../../overview/visual-cpp-samples.md)示例应用程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>要求

**标题：** afxrich.h

## <a name="cricheditcntritemcricheditcntritem"></a><a name="cricheditcntritem"></a>克里希编辑项目：：克里希编辑Cntrtr项目

调用此函数以创建对象`CRichEditCntrItem`并将其添加到容器文档。

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>参数

*普雷奥*<br/>
指向描述 OLE 项的[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)结构的指针。 新`CRichEditCntrItem`对象围绕此 OLE 项构造。 如果*Preo*为 NULL，则客户端项为空。

*pContainer*<br/>
指向将包含此项的容器文档的指针。 如果*pContainer*为 NULL，则必须显式调用[COleDocument：：addItem](../../mfc/reference/coledocument-class.md#additem)才能将此客户端项添加到文档中。

### <a name="remarks"></a>备注

此功能不执行任何 OLE 初始化。

有关详细信息，请参阅 Windows SDK 中的[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)结构。

## <a name="cricheditcntritemsynctoricheditobject"></a><a name="synctoricheditobject"></a>克里希编辑项目：：同步到里希编辑对象

调用此函数以将设备`CRichEditCntrltem`方面[DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)与*reo*指定的设备方面同步。

```
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>参数

*雷奥*<br/>
引用描述 OLE 项的[REOBJECT](/windows/win32/api/richole/ns-richole-reobject)结构。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[DVASPECT。](/windows/win32/api/wtypes/ne-wtypes-dvaspect)

## <a name="see-also"></a>另请参阅

[MFC 样品 WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem 类](../../mfc/reference/coleclientitem-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc 类](../../mfc/reference/cricheditdoc-class.md)<br/>
[克里希编辑视图类](../../mfc/reference/cricheditview-class.md)
