---
title: CMFCRibbonCustomizeDialog 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
ms.openlocfilehash: a66c0a19c04e0a900b91c0c28c45bb9c766d25c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375204"
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog 类

显示功能区 **"自定义**"页。

## <a name="syntax"></a>语法

```
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC 功能定制对话：：CMFC 功能定制对话](#cmfcribboncustomizedialog)|构造 `CMFCRibbonCustomizeDialog` 对象。|
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|`CMFCRibbonCustomizeDialog::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|

## <a name="remarks"></a>备注

如果您不处理AFX_WM_ON_RIBBON_CUSTOMIZE消息，或者从消息处理程序返回 0，MFC 会自动实例化此类。

如果要在应用程序中使用此类来显示功能区**自定义**对话框，只需实例化它并调用`DoModal`方法。

由于此类派生自[CMFC属性表类](../../mfc/reference/cmfcpropertysheet-class.md)，因此可以使用`CMFCPropertySheet`API 添加自定义页面。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

[CMFC 功能定制对话](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>要求

**标题：** afxribbon自定义对话框.h

## <a name="cmfcribboncustomizedialogcmfcribboncustomizedialog"></a><a name="cmfcribboncustomizedialog"></a>CMFC 功能定制对话：：CMFC 功能定制对话

构造 `CMFCRibbonCustomizeDialog` 对象。

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]指向父窗口（通常是主框架）的指针。

*pRibbon*<br/>
[在]要自定义的`CMFCRibbonBar`指针。

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCRibbonCustomizeDialog`对象。

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>备注

构造函数实例化[了 CMFCRibbon 自定义属性页类](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)对象，并将其添加到属性工作表页的集合中。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
