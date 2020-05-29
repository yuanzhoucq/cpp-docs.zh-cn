---
title: CMFCPropertyPage 类
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: e493f016b6384a768935186c31e3fc71ade6382f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361758"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage 类

该`CMFCPropertyPage`类支持在属性页上显示弹出式菜单。

## <a name="syntax"></a>语法

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC属性页：CMFC属性页](#cmfcpropertypage)|构造 `CMFCPropertyPage` 对象。|
|`CMFCPropertyPage::~CMFCPropertyPage`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCPropertyPage::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|`CMFCPropertyPage::OnSetActive`|当用户选择页面并成为活动页时，框架将调用此成员函数。 （覆盖[C 属性页：打开活动](../../mfc/reference/cpropertypage-class.md#onsetactive).）|
|`CMFCPropertyPage::PreTranslateMessage`|在窗口消息发送到[翻译消息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)窗口功能之前进行翻译。 有关详细信息和方法语法，请参阅[CWnd：:P重新翻译消息](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 （重写 `CPropertyPage::PreTranslateMessage`。）|

## <a name="remarks"></a>备注

类`CMFCPropertyPage`表示属性表的各个页面，也称为选项卡对话框。

将类`CMFCPropertyPage`与[CMFC 属性表](../../mfc/reference/cmfcpropertysheet-class.md)类一起使用。 要在属性页上使用菜单，请将`CPropertyPage`类的所有匹配项替换为类。 `CMFCPropertyPage`

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>要求

**标题：** afx属性页.h

## <a name="cmfcpropertypagecmfcpropertypage"></a><a name="cmfcpropertypage"></a>CMFC属性页：CMFC属性页

构造 `CMFCPropertyPage` 对象。

```
CMFCPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption=0);

CMFCPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption=0);
```

### <a name="parameters"></a>参数

*nIDTemplate*<br/>
此页模板的资源 ID。

*nIDCaption*<br/>
要放入此页选项卡中的标签的资源 ID。 如果为 0，则从此页面的对话框模板中获取该名称。 默认值为 0。

*lpszTemplate 名称*<br/>
指向此页面的模板名称。 不能为 NULL。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

有关构造函数参数的详细信息，请参阅[CPropertyPage：：CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC属性表类](../../mfc/reference/cmfcpropertysheet-class.md)
