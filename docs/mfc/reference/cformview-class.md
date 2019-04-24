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
ms.openlocfilehash: 8a0c11352ffab37f50ede5c67aa810fa20e838ed
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777267"
---
# <a name="cformview-class"></a>CFormView 类

用于窗体视图的基类。

## <a name="syntax"></a>语法

```
class CFormView : public CScrollView
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CFormView::CFormView](#cformview)|构造 `CFormView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|用于在初始化期间同步。|

## <a name="remarks"></a>备注

窗体视图是实质上是一个包含控件的视图。 这些控件基于对话框模板资源进行布局。 如果你想要你的应用程序具有窗体，请使用 `CFormView`。 这些视图支持滚动，根据需要使用[CScrollView](../../mfc/reference/cscrollview-class.md)功能。

如果要[创建基于窗体的应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)，你可以根据其视图类`CFormView`，使其基于窗体的应用程序。

此外可以插入新[窗体主题](../../mfc/form-views-mfc.md)到基于文档视图的应用程序。 即使你的应用程序最初不支持窗体，当你插入一个新窗体时 Visual C++ 将添加这一支持。

MFC 应用程序向导和“添加类”命令是创建基于窗体的应用程序的首选的方法。 如果你需要创建基于窗体的应用程序而无需使用这些方法，请参阅[创建基于窗体的应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>要求

**标头：** afxext.h

##  <a name="cformview"></a>  CFormView::CFormView

构造 `CFormView` 对象。

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>参数

*lpszTemplateName*<br/>
包含以 null 结尾的字符串，表示对话框模板资源的名称。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

### <a name="remarks"></a>备注

当创建类型的对象派生自`CFormView`，调用其中一个构造函数来创建视图对象，并确定该视图所基于的对话框资源。 按名称 （向构造函数将字符串作为参数传递） 或其 ID （将一个无符号整数作为参数传递），可以确定该资源。

窗体视图窗口和子控件之前将不创建`CWnd::Create`调用。 `CWnd::Create` 文档和视图创建过程中，这种识别由文档模板的一部分框架调用。

> [!NOTE]
>  在派生的类*必须*提供自己的构造函数。 在构造函数中，调用构造函数中， `CFormView::CFormView`，资源名称或 ID 作为参数前面类概述中所示。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

##  <a name="isinitdlgcompleted"></a>  CFormView::IsInitDlgCompleted

由 MFC 用于确保初始化完成后才会执行其他操作。

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>返回值

如果已完成了此对话框的初始化函数，则为 true。

## <a name="see-also"></a>请参阅

[MFC 示例 SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CScrollView 类](../../mfc/reference/cscrollview-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)<br/>
[CScrollView 类](../../mfc/reference/cscrollview-class.md)
