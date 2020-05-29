---
title: CFormView 类
ms.date: 11/04/2016
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
ms.openlocfilehash: a9b897c661731878f0bf78c9d04ae7c4ba28cd42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373803"
---
# <a name="cformview-class"></a>CFormView 类

用于窗体视图的基类。

## <a name="syntax"></a>语法

```
class CFormView : public CScrollView
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CFormView::CFormView](#cformview)|构造 `CFormView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|用于在初始化期间同步。|

## <a name="remarks"></a>备注

窗体视图是实质上是一个包含控件的视图。 这些控件基于对话框模板资源进行布局。 如果你想要你的应用程序具有窗体，请使用 `CFormView`。 这些视图支持根据需要使用[CScrollView](../../mfc/reference/cscrollview-class.md)功能进行滚动。

创建[基于窗体的应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)时，可以将其视图类基于`CFormView`，使其成为基于窗体的应用程序。

您还可以将新的["表单主题"](../../mfc/form-views-mfc.md)插入到基于文档视图的应用程序中。 即使你的应用程序最初不支持窗体，当你插入一个新窗体时 Visual C++ 将添加这一支持。

MFC 应用程序向导和“添加类”命令是创建基于窗体的应用程序的首选的方法。 如果需要创建基于窗体的应用程序而不使用这些方法，请参阅[创建基于窗体的应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="cformviewcformview"></a><a name="cformview"></a>CForm查看：CForm查看

构造 `CFormView` 对象。

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>参数

*lpszTemplate 名称*<br/>
包含一个 null 端接字符串，该字符串是对话框模板资源的名称。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

### <a name="remarks"></a>备注

创建派生自`CFormView`的类型的对象时，请调用其中一个构造函数来创建视图对象并标识视图所基于的对话框资源。 您可以按名称（将字符串作为参数传递给构造函数）或通过其 ID（传递未签名的整数作为参数）标识资源。

在调用窗体视图窗口和子控件之前`CWnd::Create`，不会创建窗体视图窗口和子控件。 `CWnd::Create`框架调用该框架作为文档和视图创建过程的一部分，该过程由文档模板驱动。

> [!NOTE]
> 派生类*必须*提供其自己的构造函数。 在构造函数中，调用构造函数 ，`CFormView::CFormView`将资源名称或 ID 作为参数，如前面的类概述所示。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

## <a name="cformviewisinitdlgcompleted"></a><a name="isinitdlgcompleted"></a>CFormView：IsinitDlg 完成

由 MFC 用于确保初始化完成后才会执行其他操作。

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>返回值

如果已完成了此对话框的初始化函数，则为 true。

## <a name="see-also"></a>另请参阅

[MFC 样品 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品视图](../../overview/visual-cpp-samples.md)<br/>
[CScrollView 类](../../mfc/reference/cscrollview-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView 类](../../mfc/reference/cscrollview-class.md)
