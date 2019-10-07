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
ms.openlocfilehash: 4be584135ef789d7fbe3b1743ac0ad6ce66ac5b1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505045"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage 类

`CMFCPropertyPage`类支持在属性页上显示弹出菜单。

## <a name="syntax"></a>语法

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|构造 `CMFCPropertyPage` 对象。|
|`CMFCPropertyPage::~CMFCPropertyPage`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCPropertyPage::GetThisClass`|由框架用于获取指向与此类类型相关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|`CMFCPropertyPage::OnSetActive`|当用户选择页面并成为活动页面时，框架会调用此成员函数。 （重写[CPropertyPage：： OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive)。）|
|`CMFCPropertyPage::PreTranslateMessage`|转换窗口消息，然后将其调度到[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函数。 有关详细信息和方法语法，请参阅[CWnd：:P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 （重写 `CPropertyPage::PreTranslateMessage`。）|

## <a name="remarks"></a>备注

`CMFCPropertyPage`类表示属性表的各个页，也称为选项卡对话框。

将`CMFCPropertyPage`类与 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) 类一起使用。 若要在属性页上使用菜单，请将出现`CPropertyPage`的所有类`CMFCPropertyPage`替换为类。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>要求

**标头：** afxpropertypage

##  <a name="cmfcpropertypage"></a>CMFCPropertyPage：： CMFCPropertyPage

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
此页面的模板的资源 ID。

*nIDCaption*<br/>
要放在此页的选项卡中的标签的资源 ID。 如果为0，则从该页的对话框模板获取该名称。 默认值为 0。

*lpszTemplateName*<br/>
指向此页面的模板名称。 不能为 NULL。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

有关构造函数参数的详细信息，请参阅[CPropertyPage：： CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet 类](../../mfc/reference/cmfcpropertysheet-class.md)
