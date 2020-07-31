---
title: CDaoRecordView 类
ms.date: 11/04/2016
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
helpviewer_keywords:
- CDaoRecordView [MFC], CDaoRecordView
- CDaoRecordView [MFC], IsOnFirstRecord
- CDaoRecordView [MFC], IsOnLastRecord
- CDaoRecordView [MFC], OnGetRecordset
- CDaoRecordView [MFC], OnMove
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
ms.openlocfilehash: 95ed9207d0047287e373401da52f05235a817999
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223130"
---
# <a name="cdaorecordview-class"></a>CDaoRecordView 类

显示控件中数据库记录的视图。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CDaoRecordView：： CDaoRecordView](#cdaorecordview)|构造 `CDaoRecordView` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CDaoRecordView：： IsOnFirstRecord](#isonfirstrecord)|如果当前记录是关联记录集中的第一条记录，则返回非零值。|
|[CDaoRecordView：： IsOnLastRecord](#isonlastrecord)|如果当前记录是关联记录集中的最后一条记录，则返回非零值。|
|[CDaoRecordView：： OnGetRecordset](#ongetrecordset)|返回指向派生自的类的对象的指针 `CDaoRecordset` 。 ClassWizard 将重写此函数，并在必要时创建记录集。|
|[CDaoRecordView：： OnMove](#onmove)|如果当前记录已更改，请在数据源上更新它，然后移动到指定的记录（下一个、上一个、第一个或最后一个）。|

## <a name="remarks"></a>备注

视图是直接连接到对象的窗体视图 `CDaoRecordset` 。 视图是通过对话框模板资源创建的，它 `CDaoRecordset` 在对话框模板的控件中显示对象的字段。 `CDaoRecordView`对象使用对话框数据交换（DDX）和 DAO 记录字段交换（DFX）自动在窗体上的控件和记录集的字段之间移动数据。 `CDaoRecordView`还提供移动到第一个、下一个、上一个或最后一个记录的默认实现，以及用于更新当前视图中的记录的接口。

> [!NOTE]
> DAO 数据库类与基于开放式数据库连接（ODBC）的 MFC 数据库类不同。 所有 DAO 数据库类名称都具有 "CDao" 前缀。 你仍可以使用 DAO 类访问 ODBC 数据源;DAO 类通常提供出色的功能，因为它们使用 Microsoft Jet 数据库引擎。

创建记录视图的最常见方法是通过应用程序向导。 应用程序向导创建记录视图类及其关联的记录集类作为主干入门应用程序的一部分。

如果只需要单个窗体，应用程序向导方法会更容易。 ClassWizard 可让你决定在开发过程的后期使用记录视图。 如果不通过应用程序向导创建记录视图类，以后可以通过 ClassWizard 创建它。 使用 ClassWizard 单独创建记录视图和记录集，然后连接它们是最灵活的方法，因为它使您可以更好地控制记录集类及其的名称。H/。CPP 文件。 此方法还允许您在同一个记录集类上拥有多个记录视图。

为了使最终用户能够轻松地从记录视图中的记录移动到记录，应用程序向导会创建菜单（和可选的工具栏）资源，以便移动到第一个、下一个、上一个或最后一个记录。 如果使用 ClassWizard 创建记录视图类，则需要使用菜单和位图编辑器自行创建这些资源。

有关将从记录移动到记录的默认实现的信息，请参阅 `IsOnFirstRecord` 和 `IsOnLastRecord` 和[使用记录视图](../../data/using-a-record-view-mfc-data-access.md)（适用于和）一文 `CRecordView` `CDaoRecordView` 。

`CDaoRecordView`跟踪用户在记录集中的位置，以便记录视图可以更新用户界面。 当用户移到记录集的任一端时，记录视图将禁用用户界面对象（如菜单项或工具栏按钮），以便在同一方向上进一步移动。

有关声明和使用记录视图和记录集类的详细信息，请参阅[记录](../../data/record-views-mfc-data-access.md)视图一文中的 "设计和创建记录视图"。 有关记录视图的工作原理以及如何使用它们的详细信息，请参阅[使用记录视图一](../../data/using-a-record-view-mfc-data-access.md)文。 以上提到的所有文章都适用于 `CRecordView` 和 `CDaoRecordView` 。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>要求

**标头：** afxdao

## <a name="cdaorecordviewcdaorecordview"></a><a name="cdaorecordview"></a>CDaoRecordView：： CDaoRecordView

当你创建派生自的类型的对象时 `CDaoRecordView` ，将调用构造函数的任一形式来初始化视图对象，并标识视图所基于的对话框资源。

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>参数

*lpszTemplateName*<br/>
包含以 null 结尾的字符串，它是对话框模板资源的名称。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

### <a name="remarks"></a>备注

可以按名称（将字符串作为参数传递给构造函数）或其 ID （传递无符号整数作为参数）来确定资源。 建议使用资源 ID。

> [!NOTE]
> 派生类必须提供其自己的构造函数。 在派生类的构造函数中，调用 `CDaoRecordView::CDaoRecordView` 使用资源名称或 ID 作为参数的构造函数。

`CDaoRecordView::OnInitialUpdate`调用 `CWnd::UpdateData` ，它调用 `CWnd::DoDataExchange` 。 此初始调用会 `DoDataExchange` 将 `CDaoRecordView` 控件（间接）连接到 `CDaoRecordset` 由 ClassWizard 创建的字段数据成员。 在调用基类成员函数之前，不能使用这些数据成员 `CFormView::OnInitialUpdate` 。

> [!NOTE]
> 如果使用 ClassWizard，向导将 **`enum`** `CDaoRecordView::IDD` 在类声明中定义一个值，并在构造函数的成员初始化列表中使用该值。

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

## <a name="cdaorecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CDaoRecordView：： IsOnFirstRecord

调用此成员函数以确定当前记录是否为与此记录视图关联的记录集对象中的第一条记录。

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>返回值

如果当前记录是记录集中的第一条记录，则为非零值;否则为0。

### <a name="remarks"></a>备注

此函数对于编写由 ClassWizard 编写的默认命令更新处理程序的实现非常有用。

如果用户移动到第一条记录，则框架将禁用用户界面对象（例如菜单项或工具栏按钮），您可以将这些对象移至第一个记录或上一条记录。

## <a name="cdaorecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CDaoRecordView：： IsOnLastRecord

调用此成员函数以确定当前记录是否是与此记录视图关联的记录集对象中的最后一条记录。

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>返回值

如果当前记录是记录集中的最后一条记录，则为非零值;否则为0。

### <a name="remarks"></a>备注

此函数可用于编写自己的默认命令更新处理程序的实现，这些实现 ClassWizard 写入以支持用于从记录移动到记录的用户界面。

> [!CAUTION]
> 此函数的结果是可靠的，但视图可能无法检测记录集的结尾，直到用户移过它。 用户可能必须超出最后一条记录，才能知道，记录视图必须禁用所有用户界面对象，才能移动到下一条或最后一条记录。 如果用户移过最后一条记录，然后移回最后一条记录（或之前的记录），则记录视图可以跟踪用户在记录集中的位置，并正确禁用用户界面对象。

## <a name="cdaorecordviewongetrecordset"></a><a name="ongetrecordset"></a>CDaoRecordView：： OnGetRecordset

返回一个指向 `CDaoRecordset` 与记录视图关联的派生对象的指针。

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>返回值

如果已成功创建对象，则为指向 `CDaoRecordset` 派生对象的指针; 否则为 NULL 指针。

### <a name="remarks"></a>备注

必须重写此成员函数以构造或获取记录集对象，并返回指向该对象的指针。 如果使用 ClassWizard 声明记录视图类，向导将为你写入默认替代。 ClassWizard 的默认实现返回存储在记录视图中的记录集指针（如果存在）。 如果不是，它将构造使用 ClassWizard 指定的类型的记录集对象，并调用其 `Open` 成员函数打开表或运行查询，然后返回指向对象的指针。

有关详细信息和示例，请参阅[记录视图：使用记录视图一](../../data/using-a-record-view-mfc-data-access.md)文。

## <a name="cdaorecordviewonmove"></a><a name="onmove"></a>CDaoRecordView：： OnMove

调用此成员函数可移至记录集中的其他记录，并在记录视图的控件中显示其字段。

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>参数

*nIDMoveCommand*<br/>
以下标准命令 ID 值之一：

- ID_RECORD_FIRST 移动到记录集中的第一条记录。

- ID_RECORD_LAST 移动到记录集中的最后一条记录。

- ID_RECORD_NEXT 移动到记录集中的下一条记录。

- ID_RECORD_PREV 移到记录集中的上一条记录。

### <a name="return-value"></a>返回值

如果移动成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

默认实现将调用 `CDaoRecordset` 与记录视图关联的对象的相应移动成员函数。

默认情况下， `OnMove` 如果用户已在记录视图中更改了数据源中的记录，则将更新该记录。

应用程序向导创建一个菜单资源，其中包含第一个记录、最后一个记录、下一个记录和上一个 "记录" 菜单项。 如果选择了初始工具栏选项，应用程序向导还会创建一个工具栏，其中包含与这些命令对应的按钮。

如果移过记录集中的最后一条记录，记录视图将继续显示最后一条记录。 如果向后移动第一条记录，记录视图将继续显示第一条记录。

> [!CAUTION]
> `OnMove`如果记录集没有记录，则调用会引发异常。 调用相应的用户界面更新处理程序函数（ `OnUpdateRecordFirst` 、 `OnUpdateRecordLast` 、 `OnUpdateRecordNext` 或 `OnUpdateRecordPrev` ），以确定记录集是否有任何记录。

## <a name="see-also"></a>另请参阅

[CFormView 类](../../mfc/reference/cformview-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CFormView 类](../../mfc/reference/cformview-class.md)
