---
title: CRecordView 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
dev_langs:
- C++
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23d756afd790fde4ad3bda5519a35901e043860f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432836"
---
# <a name="crecordview-class"></a>CRecordView 类

显示控件中数据库记录的视图。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CRecordView::CRecordView](#crecordview)|构造 `CRecordView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|返回非零，如果当前记录相关联的记录集中的第一个记录。|
|[CRecordView::IsOnLastRecord](#isonlastrecord)|返回非零，如果当前记录相关联的记录集中的最后一个记录。|
|[CRecordView::OnGetRecordset](#ongetrecordset)|返回指向派生自的类的对象的指针`CRecordset`。 ClassWizard 重写此函数，并创建记录集，如有必要。|
|[CRecordView::OnMove](#onmove)||

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CRecordView::OnMove](#onmove)|如果当前记录更改之后，更新数据源，则会移到指定的记录 （下一步、 上一个、 第一个或最后一个）。|

## <a name="remarks"></a>备注

该视图是直接连接到的窗体视图`CRecordset`对象。 该视图通过对话框模板资源创建和显示字段的`CRecordset`对话框模板的控件中的对象。 `CRecordView`对象使用对话框数据交换 (DDX) 和记录字段交换 (RFX) 自动执行窗体上的控件和记录集的字段之间的数据移动。 `CRecordView` 此外提供了一个默认实现来移动到第一个下, 一步上, 一个，或最后一个记录和更新当前在视图上的记录的接口。

> [!NOTE]
>  如果您正在使用的数据访问对象 (DAO) 类而不是开放式数据库连接 (ODBC) 类，使用类[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)相反。 有关详细信息，请参阅文章[概述： 数据库编程](../../data/data-access-programming-mfc-atl.md)。

若要创建记录视图的最常见方法是使用应用程序向导。 Tge 应用程序向导创建记录视图类和其关联的记录集类主干初学者应用程序的一部分。 如果不使用应用程序向导创建记录视图类，您可以创建它更高版本使用类向导。 如果您只需单个窗体，则应用程序向导方法是更容易。 类向导允许您决定更高版本在开发过程中使用记录视图。 使用类向导单独创建记录视图和记录集，并连接它们是最灵活的方法，因为这样可以更好的控制命名记录集类并将其。H /。CPP 文件。 此方法还可以有相同的记录集类上的多个记录视图。

为了方便最终用户在记录视图中移动记录，应用程序向导创建菜单 （而且还可以工具栏） 资源移到第一个下, 一步上, 一个，或最后一个记录。 如果使用类向导创建记录视图类，您需要这些资源自行创建具有菜单和位图编辑器。

有关移动记录到记录的默认实现的信息，请参阅`IsOnFirstRecord`并`IsOnLastRecord`与项目[使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。

`CRecordView` 将跟踪的记录集中的用户的位置，以便记录视图可以更新用户界面。 当用户移动到记录集的任一端时，记录视图禁用用户界面对象 — 例如菜单项或工具栏按钮 — 用于移动中相同的方向进一步。

有关声明和使用记录视图和记录集类的详细信息，请参阅"设计和创建记录视图"一文中[记录视图](../../data/record-views-mfc-data-access.md)。 有关如何记录视图的工作以及如何使用它们的详细信息，请参阅文章[使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>要求

**标头：** afxdb.h

##  <a name="crecordview"></a>  CRecordView::CRecordView

当创建类型的对象派生自`CRecordView`，调用任一格式的构造函数，以便初始化视图对象并确定该视图所基于的对话框资源。

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>参数

*lpszTemplateName*<br/>
包含以 null 结尾的字符串，表示对话框模板资源的名称。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

### <a name="remarks"></a>备注

按名称 （向构造函数将字符串作为参数传递） 或由其 ID （将一个无符号整数作为参数传递），也可以标识该资源。 被建议使用资源 ID。

> [!NOTE]
>  在派生的类*必须*提供自己的构造函数。 在派生类的构造函数中调用构造函数`CRecordView::CRecordView`与资源名称或 ID 作为参数，如下面的示例中所示。

`CRecordView::OnInitialUpdate` 调用`UpdateData`，它调用`DoDataExchange`。 此首次调用`DoDataExchange`连接`CRecordView`（间接） 为控制`CRecordset`字段数据成员创建的类向导。 之后调用基类这些成员不能使用直到`CFormView::OnInitialUpdate`成员函数。

> [!NOTE]
>  如果使用类向导，向导将定义**enum**值`CRecordView::IDD`，指定在类声明中，然后对于构造函数的成员初始化列表中使用它。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

##  <a name="isonfirstrecord"></a>  CRecordView::IsOnFirstRecord

调用此成员函数可确定当前记录是否与此记录视图关联的记录集对象中的第一个记录。

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>返回值

如果当前记录是记录集; 中的第一个记录，非零值否则为 0。

### <a name="remarks"></a>备注

此函数可用于编写自己的实现的默认命令更新处理程序编写的类向导。

如果用户移到第一条记录，框架会禁用已移动到第一个或上一条记录的任何用户界面对象。

##  <a name="isonlastrecord"></a>  CRecordView::IsOnLastRecord

调用此成员函数可确定当前记录是否与此记录视图关联的记录集对象中的最后一个记录。

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>返回值

如果当前记录是记录集; 中的最后一个记录，非零值否则为 0。

### <a name="remarks"></a>备注

此函数可用于编写自己的实现的默认 ClassWizard 写入，从而支持移动记录到记录的用户界面的命令更新处理程序。

> [!CAUTION]
>  此函数的结果是可靠的只不过直到用户已移过它，该视图无法检测到记录集的结尾。 记录视图可以告诉它必须禁用任何用户界面对象将移至下一个或最后一个记录之前，必须将用户移超出了最后一条记录。 如果用户移过最后一条记录，然后将移动回到最后一个记录 （或之前），记录视图可以跟踪中记录集的用户的位置，并正确禁用用户界面对象。 `IsOnLastRecord` 对实现函数的调用后也会不可靠`OnRecordLast`，用于处理 ID_RECORD_LAST 命令，或`CRecordset::MoveLast`。

##  <a name="ongetrecordset"></a>  CRecordView::OnGetRecordset

返回一个指向`CRecordset`-派生的与记录视图关联的对象。

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>返回值

一个指向`CRecordset`-派生对象，如果对象已成功创建; 否则为 NULL 指针。

### <a name="remarks"></a>备注

必须重写构造或获取记录集对象并返回一个指向此成员函数。 如果声明 ClassWizard 在记录视图类，该向导为您编写是默认的重写。 类向导的默认实现返回存储在记录视图中，如果存在的记录集指针。 如果不是，它构造类型的记录集对象指定与 ClassWizard 和调用其`Open`成员函数打开的表或运行查询，然后返回一个指向该对象。

有关详细信息和示例，请参阅文章[记录视图： 使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。

##  <a name="onmove"></a>  CRecordView::OnMove

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

默认实现调用适当`Move`成员函数的`CRecordset`与记录视图关联的对象。

默认情况下，`OnMove`更新数据源上的当前记录，如果用户已在记录视图中更改它。

应用程序向导会使用第一条记录、 最后一条记录下, 一条记录，以及上一条记录菜单项创建菜单资源。 如果您选择可停靠工具栏选项，应用程序向导还具有对应于这些命令的按钮创建一个工具栏。

如果您跳过在记录集中的最后一个记录，记录视图仍将显示最后一条记录。 如果您在第一条记录向后移动，记录视图仍将显示第一条记录。

> [!CAUTION]
>  调用`OnMove`将引发异常，如果记录集不具有任何记录。 调用适当的用户界面更新处理程序函数 — `OnUpdateRecordFirst`， `OnUpdateRecordLast`， `OnUpdateRecordNext`，或`OnUpdateRecordPrev`— 之前相对应移动运算来确定记录集是否具有任何记录。

## <a name="see-also"></a>请参阅

[CFormView 类](../../mfc/reference/cformview-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)<br/>
[CFormView 类](../../mfc/reference/cformview-class.md)
