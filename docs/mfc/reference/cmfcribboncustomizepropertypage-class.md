---
title: CMFC 功能定制属性页类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
ms.openlocfilehash: 57fbd1e1f574beebff8baab014e7ab615f56333f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754171"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFC 功能定制属性页类

在基于功能区的应用程序中为 **"自定义**"对话框实现自定义页面。

## <a name="syntax"></a>语法

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|[CMFC 功能自定义属性页：：CMFC 功能定制属性页](#cmfcribboncustomizepropertypage)|构造 `CMFCRibbonCustomizePropertyPage` 对象。|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[CMFC 功能自定义属性页：：添加自定义类别](#addcustomcategory)|将自定义类别添加到 **"命令**"组合框。|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFC 功能定制属性页：：OnOK](#onok)|当用户单击 **"自定义"** 对话框上的 **"确定"** 时，系统调用。|

## <a name="remarks"></a>备注

如果要将自定义命令添加到 **"自定义"** 对话框中，则必须处理AFX_WM_ON_RIBBON_CUSTOMIZE消息。 在消息处理程序中，实例化堆栈上`CMFCRibbonCustomizePropertyPage`的对象。 创建自定义命令的列表，然后调用`AddCustomCategory`以将新页面添加到 **"自定义"** 对话框中。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCRibbonCustomizePropertyPage`对象和添加自定义类别。

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMFC 功能定制属性页](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>要求

**标题：** afxribbon自定义对话框.h

## <a name="cmfcribboncustomizepropertypageaddcustomcategory"></a><a name="addcustomcategory"></a>CMFC 功能自定义属性页：：添加自定义类别

将自定义类别添加到 **"命令**"组合框。

```cpp
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*lpsz名称*|[在]指定自定义类别名称。|
|*伊斯蒂迪斯*|[在]包含要在自定义类别中显示的功能区命令 ID。|

### <a name="remarks"></a>备注

此方法将名为*lpszName 的*类别添加到**命令**组合框中。 当用户选择该类别时，*在 lstIDS*中指定的命令将显示在命令列表中。

## <a name="cmfcribboncustomizepropertypagecmfcribboncustomizepropertypage"></a><a name="cmfcribboncustomizepropertypage"></a>CMFC 功能自定义属性页：：CMFC 功能定制属性页

构造 `CMFCRibbonCustomizePropertyPage` 对象。

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>参数

*pRibbonbar*<br/>
[在]指向要自定义选项的功能区控件的指针。

## <a name="cmfcribboncustomizepropertypageonok"></a><a name="onok"></a>CMFC 功能定制属性页：：OnOK

当用户单击 **"自定义"** 对话框上的 **"确定**"时，由系统进行呼叫。

```
virtual void OnOK();
```

### <a name="remarks"></a>备注

默认实现将 **"自定义"** 对话框中选择的选项应用于"快速访问工具栏"。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
