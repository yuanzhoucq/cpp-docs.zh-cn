---
title: CRecordView 类
ms.date: 11/04/2016
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
ms.openlocfilehash: b706a80f91a3c952d80da13f453a807c775b9405
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368356"
---
# <a name="crecordview-class"></a>CRecordView 类

显示控件中数据库记录的视图。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CRecordView：CRecordView](#crecordview)|构造 `CRecordView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CRecordView：：Ison 第一记录](#isonfirstrecord)|如果当前记录是关联记录集中的第一个记录，则返回非零。|
|[CRecordView：：IslastRecord](#isonlastrecord)|如果当前记录是关联记录集中的最后一条记录，则返回非零。|
|[CRecordView：：打开记录集](#ongetrecordset)|返回指向 派生自`CRecordset`的类对象的指针。 ClassWizard 会为您重写此函数，并在必要时创建记录集。|
|[CRecordView：：移动](#onmove)||

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CRecordView：：移动](#onmove)|如果当前记录已更改，则在数据源上更新它，然后移动到指定的记录（下一个、上一个、第一个或最后一个）。|

## <a name="remarks"></a>备注

视图是直接连接到`CRecordset`对象的窗体视图。 视图是从对话框模板资源创建的，并在对话框模板的控件中显示`CRecordset`对象的字段。 对象`CRecordView`使用对话框数据交换 （DDX） 和记录字段交换 （RFX） 来自动在窗体上的控件和记录集的字段之间移动数据。 `CRecordView`还提供用于移动到第一个、下一个、上一个或最后一个记录的默认实现，以及用于更新当前查看的记录的接口。

> [!NOTE]
> 如果使用数据访问对象 （DAO） 类而不是开放数据库连接 （ODBC） 类，请使用类[CDaoRecordView。](../../mfc/reference/cdaorecordview-class.md) 有关详细信息，请参阅文章[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

创建记录视图的最常见方法是使用应用程序向导。 应用程序向导将创建记录视图类及其关联的记录集类，作为骨架初学者应用程序的一部分。 如果不使用应用程序向导创建记录视图类，则可以稍后使用 ClassWizard 创建它。 如果您只需要一个表单，则应用程序向导方法会更容易。 ClassWizard 允许您决定在开发过程的稍后时间使用记录视图。 使用 ClassWizard 分别创建记录视图和记录集，然后连接它们是最灵活的方法，因为它为您提供了命名记录集类及其 的更多控制权。H/.CPP 文件。 此方法还允许您在同一记录集类上具有多个记录视图。

为了使最终用户在记录视图中轻松从记录移动到记录，应用程序向导将创建菜单（和可选工具栏）资源，以便移动到第一、下一个、上一个或最后一个记录。 如果使用 ClassWizard 创建记录视图类，则需要使用菜单和位图编辑器自行创建这些资源。

有关从记录移动到记录的默认实现的信息，请参阅`IsOnFirstRecord`和`IsOnLastRecord`[以及文章"使用记录视图](../../data/using-a-record-view-mfc-data-access.md)"。

`CRecordView`跟踪用户在记录集中的位置，以便记录视图可以更新用户界面。 当用户移动到记录集的任一端时，记录视图将禁用用户界面对象（如菜单项或工具栏按钮）以向同一方向进一步移动。

有关声明和使用记录视图和记录集类的详细信息，请参阅文章["记录视图](../../data/record-views-mfc-data-access.md)"中的"设计和创建记录视图"。 有关记录视图的工作原理以及如何使用它们的详细信息，请参阅[文章"使用记录视图](../../data/using-a-record-view-mfc-data-access.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>要求

**标题：** afxdb.h

## <a name="crecordviewcrecordview"></a><a name="crecordview"></a>CRecordView：CRecordView

创建派生自`CRecordView`的类型的对象时，调用构造函数的任一形式来初始化视图对象并标识视图所基于的对话框资源。

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>参数

*lpszTemplate 名称*<br/>
包含一个 null 端接字符串，该字符串是对话框模板资源的名称。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

### <a name="remarks"></a>备注

您可以按名称标识资源（将字符串作为参数传递给构造函数）或通过其 ID（传递未签名的整数作为参数）。 建议使用资源 ID。

> [!NOTE]
> 派生类*必须*提供其自己的构造函数。 在派生类的构造函数中，将资源名称或`CRecordView::CRecordView`ID 的构造函数称为参数，如下例所示。

`CRecordView::OnInitialUpdate`调用`UpdateData`，调用`DoDataExchange`。 此初始调用将`DoDataExchange`控件`CRecordView`（间接）连接到`CRecordset`ClassWizard 创建的字段数据成员。 在调用基类`CFormView::OnInitialUpdate`成员函数之前，不能使用这些数据成员。

> [!NOTE]
> 如果使用 ClassWizard，向导将定义**枚举**值`CRecordView::IDD`，在类声明中指定它，并在构造函数的成员初始化列表中使用它。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

## <a name="crecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CRecordView：：Ison 第一记录

调用此成员函数以确定当前记录是否是与此记录视图关联的记录集对象中的第一个记录。

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>返回值

如果当前记录是记录集中的第一个记录，则非零;否则 0。

### <a name="remarks"></a>备注

此函数可用于编写由 ClassWizard 编写的默认命令更新处理程序的实现。

如果用户移动到第一条记录，框架将禁用移动到第一条或上一条记录时具有的任何用户界面对象。

## <a name="crecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CRecordView：：IslastRecord

调用此成员函数以确定当前记录是否是与此记录视图关联的记录集对象中的最后一条记录。

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>返回值

如果当前记录是记录集中的最后一条记录，则非零;否则 0。

### <a name="remarks"></a>备注

此函数可用于编写 ClassWizard 编写的默认命令更新处理程序的实现，以支持用户界面从记录移动到记录。

> [!CAUTION]
> 此功能的结果是可靠的，只不过视图在用户移动过去记录集之前无法检测到记录集的末尾。 用户必须超越最后一条记录，记录视图才能判断它必须禁用任何用户界面对象才能移动到下一条或最后一条记录。 如果用户移动过去最后一条记录，然后移回最后一条记录（或之前），记录视图可以跟踪用户在记录集中的位置并正确禁用用户界面对象。 `IsOnLastRecord`对处理ID_RECORD_LAST命令的`OnRecordLast``CRecordset::MoveLast`实现函数的调用后也不可靠。

## <a name="crecordviewongetrecordset"></a><a name="ongetrecordset"></a>CRecordView：：打开记录集

返回指向与记录视图`CRecordset`关联的派生对象的指针。

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>返回值

如果成功创建了对象`CRecordset`，则指向派生对象的指针;否则为 NULL 指针。

### <a name="remarks"></a>备注

必须重写此成员函数以构造或获取记录集对象，并返回指向它的指针。 如果使用 ClassWizard 声明记录视图类，向导将为您编写默认覆盖。 ClassWizard 的默认实现返回存储在记录视图中的记录集指针（如果存在）。 如果没有，它将构造使用 ClassWizard 指定的类型的记录集对象，并调用其成员`Open`函数打开表或运行查询，然后返回指向该对象的指针。

有关详细信息和示例，请参阅[文章记录视图：使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。

## <a name="crecordviewonmove"></a><a name="onmove"></a>CRecordView：：移动

调用此成员函数以移动到记录集中的不同记录，并在记录视图的控件中显示其字段。

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>参数

*nIDMove命令*<br/>
以下标准命令 ID 值之一：

- ID_RECORD_FIRST移动到记录集中的第一个记录。

- ID_RECORD_LAST移动到记录集中的最后一条记录。

- ID_RECORD_NEXT移动到记录集中的下一个记录。

- ID_RECORD_PREV移动到记录集中的上一条记录。

### <a name="return-value"></a>返回值

如果移动成功，则非零;否则 0 如果移动请求被拒绝。

### <a name="remarks"></a>备注

默认实现调用与记录视图`Move`关联的`CRecordset`对象的相应成员函数。

默认情况下，`OnMove`如果用户在记录视图中更改了数据源上的当前记录，则更新该记录。

"应用程序向导"创建具有"第一条记录"、"最后一条记录"、"下一个记录"和"上一个记录"菜单项的菜单资源。 如果选择"可停靠工具栏"选项，则"应用程序向导"还会创建一个工具栏，其中按钮对应于这些命令。

如果移动超过记录集中的最后一条记录，记录视图将继续显示最后一条记录。 如果向后移动超过第一条记录，则记录视图将继续显示第一条记录。

> [!CAUTION]
> 如果`OnMove`记录集没有记录，则调用将引发异常。 在相应的移动操作之前调用相应的用户界面更新`OnUpdateRecordFirst`处理程序`OnUpdateRecordLast`函数`OnUpdateRecordNext`* `OnUpdateRecordPrev` 、 、 、 或 " 以确定记录集是否具有任何记录。

## <a name="see-also"></a>另请参阅

[CFormView 类](../../mfc/reference/cformview-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 类](../../mfc/reference/crecordset-class.md)<br/>
[CFormView 类](../../mfc/reference/cformview-class.md)
