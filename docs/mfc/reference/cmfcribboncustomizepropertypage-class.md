---
title: CMFCRibbonCustomizePropertyPage 类
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
ms.openlocfilehash: f667310208d88dff39364de480309b4bfea71d16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648079"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage 类

实现的自定义页面**自定义**基于功能区的应用程序的对话框。

## <a name="syntax"></a>语法

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|描述|
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|构造 `CMFCRibbonCustomizePropertyPage` 对象。|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|描述|
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|添加到自定义类别**命令**组合框。|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|由系统调用，当用户单击**确定**上**自定义**对话框。|

## <a name="remarks"></a>备注

如果你想要添加到自定义命令**自定义**对话框中，你必须处理 AFX_WM_ON_RIBBON_CUSTOMIZE 消息。 在消息处理程序中，实例化`CMFCRibbonCustomizePropertyPage`在堆栈上的对象。 创建自定义命令的列表，然后调用`AddCustomCategory`要添加到新页面**自定义**对话框。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCRibbonCustomizePropertyPage`对象，并将添加一个自定义类别。

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>要求

**标头：** afxribboncustomizedialog.h

##  <a name="addcustomcategory"></a>  CMFCRibbonCustomizePropertyPage::AddCustomCategory

添加到自定义类别**命令**组合框。

```
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*lpszName*|[in]指定自定义类别名称。|
|*lstIDS*|[in]包含功能区命令 Id 的自定义的类别中显示。|

### <a name="remarks"></a>备注

此方法将添加一个名为类别*lpszName*到**命令**组合框。 当用户选择类别时，这些命令中指定*lstIDS*命令列表中显示。

##  <a name="cmfcribboncustomizepropertypage"></a>  CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

构造 `CMFCRibbonCustomizePropertyPage` 对象。

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>参数

*pRibbonBar*<br/>
[in]指向要为其功能区控件的自定义的选项。

##  <a name="onok"></a>  CMFCRibbonCustomizePropertyPage::OnOK

当用户单击系统 Calleld**确定**上**自定义**对话框。

```
virtual void OnOK();
```

### <a name="remarks"></a>备注

默认实现将应用中选择的选项**自定义**对话框，以便快速访问工具栏。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
