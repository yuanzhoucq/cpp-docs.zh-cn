---
title: COleDBRecordView 类
ms.date: 11/04/2016
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
ms.openlocfilehash: de9c602cb747ee3d4449df479530e55ce907cb8a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366108"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView 类

显示控件中数据库记录的视图。

## <a name="syntax"></a>语法

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[COleDB记录视图：COleDB记录视图](#coledbrecordview)|构造 `COleDBRecordView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleDB 记录视图：：OnGetRowset](#ongetrowset)|返回标准 HRESULT 值。|
|[COleDB 记录视图：：移动](#onmove)|更新数据源上的当前记录（如果脏），然后移动到指定的记录（下一个、上一个、第一个或最后一个）。|

## <a name="remarks"></a>备注

视图是直接连接到`CRowset`对象的窗体视图。 视图是从对话框模板资源创建的，并在对话框模板的控件中显示`CRowset`对象的字段。 对象`COleDBRecordView`使用对话框数据交换 （DDX） 和 内置`CRowset`的导航功能来自动在窗体上的控件和行集的字段之间移动数据。 `COleDBRecordView`还提供用于移动到第一个、下一个、上一个或最后一个记录的默认实现，以及用于更新当前查看的记录的接口。

您可以使用 DDX 函数`COleDbRecordView`直接从数据库记录集中获取数据，并将其显示在对话框控件中。 应使用`DDX_*``DDX_Text`方法（如 ），而不是 使用`DDX_Field*``DDX_FieldText``COleDbRecordView`的函数（如 ）。 `DDX_FieldText`将不起作用`COleDbRecordView`，因为`DDX_FieldText`需要键入`CRecordset*``CRecordView`（） 或`CDaoRecordset*`（的`CDaoRecordView`） 的其他参数。

> [!NOTE]
> 如果使用数据访问对象 （DAO） 类而不是 OLE DB 使用者模板类，请使用类[CDaoRecordView。](../../mfc/reference/cdaorecordview-class.md) 有关详细信息，请参阅文章[概述：数据库编程](../../data/data-access-programming-mfc-atl.md)。

`COleDBRecordView`跟踪用户在行集中的位置，以便记录视图可以更新用户界面。 当用户移动到行集的任一端时，记录视图将禁用用户界面对象（如菜单项或工具栏按钮）以向同一方向进一步移动。

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

**标题：** afxoledb.h

## <a name="coledbrecordviewcoledbrecordview"></a><a name="coledbrecordview"></a>COleDB记录视图：COleDB记录视图

构造 `COleDBRecordView` 对象。

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>参数

*lpszTemplate 名称*<br/>
包含一个 null 端接字符串，该字符串是对话框模板资源的名称。

*nIDTemplate*<br/>
包含对话框模板资源的 ID 号。

### <a name="remarks"></a>备注

创建派生自`COleDBRecordView`的类型的对象时，请调用其中一个构造函数来创建视图对象并标识视图所基于的对话框资源。 您可以按名称（将字符串作为参数传递给构造函数）或通过其 ID（传递未签名的整数作为参数）标识资源。

> [!NOTE]
> 派生类*必须*提供其自己的构造函数。 在构造函数中，调用构造函数 ，`COleDBRecordView::COleDBRecordView`将资源名称或 ID 作为参数。

## <a name="coledbrecordviewongetrowset"></a><a name="ongetrowset"></a>COleDB 记录视图：：OnGetRowset

返回与记录视图关联的**CRowset<>** 对象的句柄。

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

必须重写此成员函数以构造或获取行集对象，并将句柄返回给该对象。 如果使用 ClassWizard 声明记录视图类，向导将为您编写默认覆盖。 ClassWizard 的默认实现返回存储在记录视图中的行集句柄（如果存在）。 如果没有，它将构造使用 ClassWizard 指定的类型的排集对象，并调用其成员`Open`函数打开表或运行查询，然后向该对象返回句柄。

> [!NOTE]
> 在 MFC 7.0`OnGetRowset`之前，返回`CRowset`指向 的指针。 如果代码调用`OnGetRowset`，则需要将返回类型更改为临时化类**CRowset<>**。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

有关详细信息和示例，请参阅[文章记录视图：使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。

## <a name="coledbrecordviewonmove"></a><a name="onmove"></a>COleDB 记录视图：：移动

移动到行集中中的不同记录，并在记录视图的控件中显示其字段。

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>参数

*nIDMove命令*<br/>
以下标准命令 ID 值之一：

- ID_RECORD_FIRST = 移动到记录集中的第一个记录。

- ID_RECORD_LAST = 移动到记录集中的最后一个记录。

- ID_RECORD_NEXT = 移动到记录集中的下一个记录。

- ID_RECORD_PREV = 移动到记录集中的上一条记录。

### <a name="return-value"></a>返回值

如果移动成功，则非零;否则 0 如果移动请求被拒绝。

### <a name="remarks"></a>备注

默认实现调用与记录视图`Move`关联的`CRowset`对象的相应成员函数。

默认情况下，`OnMove`如果用户在记录视图中更改了数据源上的当前记录，则更新该记录。

"应用程序向导"创建具有"第一条记录"、"最后一条记录"、"下一个记录"和"上一个记录"菜单项的菜单资源。 如果选择"可停靠工具栏"选项，"应用程序向导"还会创建一个工具栏，其中按钮对应于这些命令。

如果移动超过记录集中的最后一条记录，记录视图将继续显示最后一条记录。 如果向后移动超过第一条记录，则记录视图将继续显示第一条记录。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)
