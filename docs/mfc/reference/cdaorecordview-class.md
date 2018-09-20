---
title: CDaoRecordView 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
dev_langs:
- C++
helpviewer_keywords:
- CDaoRecordView [MFC], CDaoRecordView
- CDaoRecordView [MFC], IsOnFirstRecord
- CDaoRecordView [MFC], IsOnLastRecord
- CDaoRecordView [MFC], OnGetRecordset
- CDaoRecordView [MFC], OnMove
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78d0dd3715ceb6a366ae1ab9ef2c2104432b30af
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446085"
---
# <a name="cdaorecordview-class"></a>CDaoRecordView 类

显示控件中数据库记录的视图。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CDaoRecordView::CDaoRecordView](#cdaorecordview)|构造 `CDaoRecordView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDaoRecordView::IsOnFirstRecord](#isonfirstrecord)|返回非零，如果当前记录相关联的记录集中的第一个记录。|
|[CDaoRecordView::IsOnLastRecord](#isonlastrecord)|返回非零，如果当前记录相关联的记录集中的最后一个记录。|
|[CDaoRecordView::OnGetRecordset](#ongetrecordset)|返回指向派生自的类的对象的指针`CDaoRecordset`。 ClassWizard 重写此函数，并创建记录集，如有必要。|
|[CDaoRecordView::OnMove](#onmove)|如果当前记录更改之后，更新数据源，则会移到指定的记录 （下一步、 上一个、 第一个或最后一个）。|

## <a name="remarks"></a>备注

该视图是直接连接到的窗体视图`CDaoRecordset`对象。 该视图通过对话框模板资源创建和显示字段的`CDaoRecordset`对话框模板的控件中的对象。 `CDaoRecordView`对象使用对话框数据交换 (DDX) 和 DAO 记录字段交换 (DFX) 自动执行窗体上的控件和记录集的字段之间的数据移动。 `CDaoRecordView` 此外提供了一个默认实现来移动到第一个下, 一步上, 一个，或最后一个记录和更新当前在视图中的记录的接口。

> [!NOTE]
>  DAO 数据库类是不同于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 所有 DAO 数据库类名称都具有"CDao"前缀。 您仍然可以访问 ODBC 数据源对于 DAO 类中;DAO 类通常提供高级功能，因为它们使用 Microsoft Jet 数据库引擎。

若要创建记录视图的最常见方法是使用应用程序向导。 应用程序向导创建记录视图类和其关联的记录集类主干初学者应用程序的一部分。

如果您只需单个窗体，则应用程序向导方法是更容易。 类向导允许您决定更高版本在开发过程中使用记录视图。 如果不使用应用程序向导创建记录视图类，您可以创建它更高版本使用类向导。 使用类向导单独创建记录视图和记录集，并连接它们是最灵活的方法，因为这样可以更好的控制命名记录集类并将其。H /。CPP 文件。 此方法还可以有相同的记录集类上的多个记录视图。

为了方便最终用户在记录视图中移动记录，应用程序向导创建菜单 （而且还可以工具栏） 资源移到第一个下, 一步上, 一个，或最后一个记录。 如果使用类向导创建记录视图类，您需要这些资源自行创建具有菜单和位图编辑器。

有关移动记录到记录的默认实现的信息，请参阅`IsOnFirstRecord`并`IsOnLastRecord`与项目[使用记录视图](../../data/using-a-record-view-mfc-data-access.md)，这同时适用于`CRecordView`和`CDaoRecordView`。

`CDaoRecordView` 将跟踪的记录集中的用户的位置，以便记录视图可以更新用户界面。 当用户移动到记录集的任一端时，记录视图禁用用户界面对象 — 例如菜单项或工具栏按钮 — 用于移动中相同的方向进一步。

有关声明和使用记录视图和记录集类的详细信息，请参阅"设计和创建记录视图"一文中[记录视图](../../data/record-views-mfc-data-access.md)。 有关如何记录视图的工作以及如何使用它们的详细信息，请参阅文章[使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。 上面提到的所有文章都适用于`CRecordView`和`CDaoRecordView`。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>要求

**标头：** afxdao.h

##  <a name="cdaorecordview"></a>  CDaoRecordView::CDaoRecordView

当创建类型的对象派生自`CDaoRecordView`，调用任一格式的构造函数，以便初始化视图对象并确定该视图所基于的对话框资源。

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>参数

*lpszTemplateName*<br/>
包含以 null 结尾的字符串，表示对话框模板资源的名称。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

### <a name="remarks"></a>备注

按名称 （向构造函数将字符串作为参数传递） 或由其 ID （将一个无符号整数作为参数传递），也可以标识该资源。 被建议使用资源 ID。

> [!NOTE]
>  在派生的类必须提供自己的构造函数。 在派生类的构造函数中调用构造函数`CDaoRecordView::CDaoRecordView`与资源名称或 ID 作为参数。

`CDaoRecordView::OnInitialUpdate` 调用`CWnd::UpdateData`，它调用`CWnd::DoDataExchange`。 此首次调用`DoDataExchange`连接`CDaoRecordView`（间接） 为控制`CDaoRecordset`字段数据成员创建的类向导。 之后调用基类这些成员不能使用直到`CFormView::OnInitialUpdate`成员函数。

> [!NOTE]
>  如果使用类向导，向导将定义**enum**值`CDaoRecordView::IDD`类声明和使用它的成员初始化中列出的构造函数中。

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

##  <a name="isonfirstrecord"></a>  CDaoRecordView::IsOnFirstRecord

调用此成员函数可确定当前记录是否与此记录视图关联的记录集对象中的第一个记录。

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>返回值

如果当前记录是记录集; 中的第一个记录，非零值否则为 0。

### <a name="remarks"></a>备注

此函数可用于编写自己的实现的默认命令更新处理程序编写的类向导。

如果用户移到第一条记录，framework 禁用任何用户界面对象 （如菜单项或工具栏按钮） 则必须将移动到第一个或上一条记录。

##  <a name="isonlastrecord"></a>  CDaoRecordView::IsOnLastRecord

调用此成员函数可确定当前记录是否与此记录视图关联的记录集对象中的最后一个记录。

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>返回值

如果当前记录是记录集; 中的最后一个记录，非零值否则为 0。

### <a name="remarks"></a>备注

此函数可用于编写自己的实现的默认 ClassWizard 写入，从而支持移动记录到记录的用户界面的命令更新处理程序。

> [!CAUTION]
>  此函数的结果是可靠的只不过此视图不可能能够检测到记录集的结尾，直到用户已移过它。 用户可能必须移动超出最后一个记录之前记录的视图可以告诉它必须禁用任何用户界面对象将移至下一个或最后一个记录。 如果用户移过最后一条记录，然后将移动回到最后一个记录 （或之前），记录视图可以跟踪中记录集的用户的位置，并正确禁用用户界面对象。

##  <a name="ongetrecordset"></a>  CDaoRecordView::OnGetRecordset

返回一个指向`CDaoRecordset`-派生的与记录视图关联的对象。

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>返回值

一个指向`CDaoRecordset`-派生对象，如果对象已成功创建; 否则为 NULL 指针。

### <a name="remarks"></a>备注

必须重写构造或获取记录集对象并返回一个指向此成员函数。 如果声明 ClassWizard 在记录视图类，该向导为您编写是默认的重写。 类向导的默认实现返回存储在记录视图中，如果存在的记录集指针。 如果不是，它构造类型的记录集对象指定与 ClassWizard 和调用其`Open`成员函数打开的表或运行查询，然后返回一个指向该对象。

有关详细信息和示例，请参阅文章[记录视图： 使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。

##  <a name="onmove"></a>  CDaoRecordView::OnMove

调用此成员函数以将移动到另一条记录中记录集和记录视图控件中显示其字段。

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>参数

*nIDMoveCommand*<br/>
以下标准命令 ID 值之一：

- ID_RECORD_FIRST 将移动到记录集中的第一个记录。

- ID_RECORD_LAST 将移动到记录集中的最后一个记录。

- ID_RECORD_NEXT 将移动到记录集的下一个记录。

- ID_RECORD_PREV 将移到上一记录中记录集。

### <a name="return-value"></a>返回值

如果移动不成功，则非零值否则为 0，如果移动请求被拒绝。

### <a name="remarks"></a>备注

默认实现调用相应的移动成员函数的`CDaoRecordset`与记录视图关联的对象。

默认情况下，`OnMove`更新数据源上的当前记录，如果用户已在记录视图中更改它。

应用程序向导会使用第一条记录、 最后一条记录下, 一条记录，以及上一条记录菜单项创建菜单资源。 如果您选择初始工具栏选项，应用程序向导还具有对应于这些命令的按钮创建一个工具栏。

如果您跳过在记录集中的最后一个记录，记录视图仍将显示最后一条记录。 如果您在第一条记录向后移动，记录视图仍将显示第一条记录。

> [!CAUTION]
>  调用`OnMove`将引发异常，如果记录集不具有任何记录。 调用适当的用户界面更新处理程序函数 — `OnUpdateRecordFirst`， `OnUpdateRecordLast`， `OnUpdateRecordNext`，或`OnUpdateRecordPrev`— 之前相对应移动运算来确定记录集是否具有任何记录。

## <a name="see-also"></a>请参阅

[CFormView 类](../../mfc/reference/cformview-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CFormView 类](../../mfc/reference/cformview-class.md)
