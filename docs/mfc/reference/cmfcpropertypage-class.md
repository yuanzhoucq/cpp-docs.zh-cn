---
title: CMFCPropertyPage 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6bbfce70e33441c1713a2297ca925e83e6cbba9f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427142"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage 类

`CMFCPropertyPage`类支持的属性页上的弹出菜单显示。

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
|`CMFCPropertyPage::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|`CMFCPropertyPage::OnSetActive`|用户选择和成为活动页的页时，由框架调用此成员函数。 (重写[cpropertypage:: Onsetactive](../../mfc/reference/cpropertypage-class.md#onsetactive)。)|
|`CMFCPropertyPage::PreTranslateMessage`|将窗口消息调度到之前[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)并[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函数。 有关详细信息和方法语法，请参阅[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 （重写 `CPropertyPage::PreTranslateMessage`。）|

## <a name="remarks"></a>备注

`CMFCPropertyPage`类表示属性表，也称为选项卡对话框中的各个页。

使用`CMFCPropertyPage`类一起[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)类。 若要使用的属性页上的菜单，替换出现的所有`CPropertyPage`类的`CMFCPropertyPage`类。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>要求

**标头：** afxpropertypage.h

##  <a name="cmfcpropertypage"></a>  CMFCPropertyPage::CMFCPropertyPage

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
此页的模板的资源 ID。

*nIDCaption*<br/>
资源的标签的 ID 以放入此页的选项卡。 如果为 0，则从的此页的对话框模板获取名称。 默认值为 0。

*lpszTemplateName*<br/>
指向此页面的模板的名称。 不能为 NULL。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

有关构造函数参数的详细信息，请参阅[CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet 类](../../mfc/reference/cmfcpropertysheet-class.md)
