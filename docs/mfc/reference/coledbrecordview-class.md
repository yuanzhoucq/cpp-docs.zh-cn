---
title: COleDBRecordView 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
dev_langs:
- C++
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae0d531930a2cfbb00be5bc0fb9a043a10e7d9f2
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059059"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView 类

显示控件中数据库记录的视图。

## <a name="syntax"></a>语法

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|构造 `COleDBRecordView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleDBRecordView::OnGetRowset](#ongetrowset)|返回一个标准的 HRESULT 值。|
|[COleDBRecordView::OnMove](#onmove)|当前记录 （如果更新），可以在更新数据源，然后移动到指定的记录 （下一步、 上一个、 第一个或最后一个）。|

## <a name="remarks"></a>备注

该视图是直接连接到的窗体视图`CRowset`对象。 该视图通过对话框模板资源创建和显示字段的`CRowset`对话框模板的控件中的对象。 `COleDBRecordView`对象使用对话框数据交换 (DDX) 和导航功能内置到`CRowset`，以自动执行窗体上的控件和行集的字段之间的数据移动。 `COleDBRecordView` 此外提供了一个默认实现来移动到第一个下, 一步上, 一个，或最后一个记录和更新当前在视图上的记录的接口。

您可以使用 DDX 函数与`COleDbRecordView`以直接从数据库记录集获取数据并将其显示在对话框控件。 应使用`DDX_*`方法 (如`DDX_Text`)，而非`DDX_Field*`函数 (如`DDX_FieldText`) 与`COleDbRecordView`。 `DDX_FieldText` 不会使用`COleDbRecordView`因为`DDX_FieldText`使用类型的其他参数`CRecordset*`(对于`CRecordView`) 或`CDaoRecordset*`(为`CDaoRecordView`)。

> [!NOTE]
>  如果您正在使用的数据访问对象 (DAO) 类而不是 OLE DB 使用者模板类，使用类[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)相反。 有关详细信息，请参阅文章[概述： 数据库编程](../../data/data-access-programming-mfc-atl.md)。

`COleDBRecordView` 将跟踪的行集中的用户的位置，以便记录视图可以更新用户界面。 当用户移动到行集中的任一端时，记录视图禁用用户界面对象 — 例如菜单项或工具栏按钮 — 用于移动中相同的方向进一步。

有关行集类的详细信息，请参阅[使用 OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)一文。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>要求

**标头：** afxoledb.h

##  <a name="coledbrecordview"></a>  COleDBRecordView::COleDBRecordView

构造 `COleDBRecordView` 对象。

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>参数

*lpszTemplateName*<br/>
包含以 null 结尾的字符串，表示对话框模板资源的名称。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

### <a name="remarks"></a>备注

当创建类型的对象派生自`COleDBRecordView`，调用其中一个构造函数来创建视图对象，并确定该视图所基于的对话框资源。 按名称 （向构造函数将字符串作为参数传递） 或其 ID （将一个无符号整数作为参数传递），可以确定该资源。

> [!NOTE]
>  在派生的类*必须*提供自己的构造函数。 在构造函数中，调用构造函数中， `COleDBRecordView::COleDBRecordView`，资源名称或 ID 作为参数。

##  <a name="ongetrowset"></a>  COleDBRecordView::OnGetRowset

返回的句柄**CRowset <>** 与记录视图关联的对象。

```
virtual CRowset<>* OnGetRowset() = 0;

```

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

必须重写此成员函数以构造或获取行集对象并返回一个句柄。 如果声明 ClassWizard 在记录视图类，该向导为您编写是默认的重写。 类向导的默认实现返回存储在记录视图中，如果存在的行集句柄。 如果不是，它构造类型的行集对象指定与 ClassWizard 和调用其`Open`成员函数打开的表或运行查询，然后返回该对象的句柄。

> [!NOTE]
>  上一步 MFC 7.0`OnGetRowset`返回一个指向`CRowset`。 如果必须调用的代码`OnGetRowset`，您需要返回类型更改为模板化类**CRowset <>**。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

有关详细信息和示例，请参阅文章[记录视图： 使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。

##  <a name="onmove"></a>  COleDBRecordView::OnMove

转到另一条记录中的行集和显示其字段中记录的控件视图。

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>参数

*nIDMoveCommand*<br/>
以下标准命令 ID 值之一：

- ID_RECORD_FIRST — 将移动到记录集中的第一个记录。

- ID_RECORD_LAST — 移动到最后一个记录中记录集。

- ID_RECORD_NEXT — 将移动到记录集的下一个记录。

- ID_RECORD_PREV — 将移到上一记录中记录集。

### <a name="return-value"></a>返回值

如果移动不成功，则非零值否则为 0，如果移动请求被拒绝。

### <a name="remarks"></a>备注

默认实现调用适当`Move`成员函数的`CRowset`与记录视图关联的对象。

默认情况下，`OnMove`更新数据源上的当前记录，如果用户已在记录视图中更改它。

应用程序向导会使用第一条记录、 最后一条记录下, 一条记录，以及上一条记录菜单项创建菜单资源。 如果您选择可停靠工具栏选项，应用程序向导还具有对应于这些命令的按钮创建一个工具栏。

如果您跳过在记录集中的最后一个记录，记录视图仍将显示最后一条记录。 如果您在第一条记录向后移动，记录视图仍将显示第一条记录。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)

