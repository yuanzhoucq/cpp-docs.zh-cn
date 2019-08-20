---
title: CRichEditDoc 类
ms.date: 11/04/2016
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
ms.openlocfilehash: d296185fe2ea2216f4abe17b191f71b6fa36e1f9
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916708"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc 类

对于[CRichEditView](../../mfc/reference/cricheditview-class.md)和[CRICHEDITCNTRITEM](../../mfc/reference/cricheditcntritem-class.md), 提供 MFC 文档视图体系结构上下文中 rich edit 控件的功能。

## <a name="syntax"></a>语法

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|调用以执行文档清理。|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|指示流输入和输出是否应包含格式设置信息。|
|[CRichEditDoc::GetView](#getview)|检索 asssociated [CRichEditView](../../mfc/reference/cricheditview-class.md)对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|指示流 i/o 是否应包括格式设置。|

## <a name="remarks"></a>备注

"Rich edit 控件" 是用户可在其中输入和编辑文本的窗口。 可以为文本分配字符和段落格式, 还可以包括嵌入的 OLE 对象。 Rich edit 控件提供了用于设置文本格式的编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。

`CRichEditView` 保留文本及其格式特征。 `CRichEditDoc`维护视图中的客户端项的列表。 `CRichEditCntrItem`提供对 OLE 客户端项的容器端访问。

此 Windows 公共控件 (以及[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相关类) 仅适用于在 windows 95/98 和 windows NT 版本3.51 及更高版本下运行的程序。

有关在 MFC 应用程序中使用丰富编辑文档的示例, 请参阅[写字板](../../overview/visual-cpp-samples.md)示例应用程序。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>要求

**标头:** afxrich

##  <a name="createclientitem"></a>CRichEditDoc:: CreateClientItem

调用此函数可创建`CRichEditCntrItem`对象并将其添加到此文档中。

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>参数

*preo*<br/>
指向描述 OLE 项的[REOBJECT](/windows/desktop/api/richole/ns-richole-reobject)结构的指针。 围绕此`CRichEditCntrItem` OLE 项构造新的对象。 如果*preo*为 NULL, 则新的客户端项为空。

### <a name="return-value"></a>返回值

指向已添加到此文档中的新[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)对象的指针。

### <a name="remarks"></a>备注

此函数不执行任何 OLE 初始化。

有关详细信息, 请参阅 Windows SDK 中的[REOBJECT](/windows/desktop/api/richole/ns-richole-reobject)结构。

##  <a name="getstreamformat"></a>CRichEditDoc:: GetStreamFormat

调用此函数可确定用于流式传输丰富编辑内容的文本格式。

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>返回值

下列标志之一:

- SF_TEXT 指示 rtf 编辑控件不维护格式设置信息。

- SF_RTF 指示 rich edit 控件确实维护格式设置信息。

### <a name="remarks"></a>备注

返回值基于[m_bRTF](#m_brtf)数据成员。 如果`m_bRTF`为 TRUE, 则此函数将返回 SF_RTF; 否则返回 SF_TEXT。

##  <a name="getview"></a>CRichEditDoc:: GetView

调用此函数可访问与此`CRichEditDoc`对象关联的 [CRichEditView](../../mfc/reference/cricheditview-class.md) 对象。

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>返回值

指向与文档`CRichEditView`关联的对象的指针。

### <a name="remarks"></a>备注

文本和格式设置信息包含在`CRichEditView`对象内。 `CRichEditDoc`对象维护用于序列化的 OLE 项。 每个`CRichEditView` `CRichEditDoc`只能有一个。

##  <a name="m_brtf"></a>CRichEditDoc:: m_bRTF

如果为 TRUE, 则指示[CRichEditCtrl:: StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin)和[CRichEditCtrl:: StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout)应存储段落和字符格式特性。

```
BOOL m_bRTF;
```

## <a name="see-also"></a>请参阅

[MFC 示例写字板](../../overview/visual-cpp-samples.md)<br/>
[COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView 类](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem 类](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument 类](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl 类](../../mfc/reference/cricheditctrl-class.md)
