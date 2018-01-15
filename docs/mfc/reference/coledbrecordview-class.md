---
title: "COleDBRecordView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
dev_langs: C++
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dd827d729af5186d6872536cdaa3d8863d1f8d10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[COleDBRecordView::OnGetRowset](#ongetrowset)|返回一个标准`HRESULT`值。|  
|[COleDBRecordView::OnMove](#onmove)|当前记录 （如果更新），可以在更新数据源，然后移动到指定的记录 （下一步、 上一个、 第一个或最后一个）。|  
  
## <a name="remarks"></a>备注  
 视图是直接连接到窗体视图`CRowset`对象。 该视图通过对话框模板资源创建和显示的字段`CRowset`对话框模板的控件中的对象。 `COleDBRecordView`对象使用对话框数据交换 (DDX) 和导航功能内置于`CRowset`，以自动进行的窗体上的控件和行集的字段之间的数据移动。 `COleDBRecordView`此外提供了一个默认实现来移动第一个下, 一步上, 一个或最后一个记录和用于更新当前上视图的记录的接口。  
  
 您可以使用与的 DDX 函数**COleDbRecordView**直接从数据库记录集获取数据并将其显示在对话框控件。 应使用**DDX_\*** 方法 (如`DDX_Text`)，而不**DDX_Field\*** 函数 (如`DDX_FieldText`) 与**COleDbRecordView**. `DDX_FieldText`不会使用**COleDbRecordView**因为`DDX_FieldText`采用类型的其他自变量**CRecordset\***  (有关`CRecordView`) 或**CDaoRecordset\***  (有关`CDaoRecordView`)。  
  
> [!NOTE]
>  如果你正在使用的数据访问对象 (DAO) 类，而不是 OLE DB 使用者模板类，可以使用类[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)相反。 有关详细信息，请参阅文章[概述： 数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 `COleDBRecordView`将跟踪的行集中的用户的位置，以便记录视图可以更新用户界面。 如果用户移到行集中的任意一端，记录视图禁用用户界面对象 — 如菜单项或工具栏按钮-移动进一步方向相同。  
  
 有关行集类的详细信息，请参阅[使用 OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)文章。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `COleDBRecordView`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxoledb.h  
  
##  <a name="coledbrecordview"></a>COleDBRecordView::COleDBRecordView  
 构造 `COleDBRecordView` 对象。  
  
```  
COleDBRecordView(LPCTSTR lpszTemplateName);  
COleDBRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>参数  
 `lpszTemplateName`  
 包含是对话框模板资源的名称的以 null 结尾的字符串。  
  
 `nIDTemplate`  
 包含对话框模板资源的 ID 号。  
  
### <a name="remarks"></a>备注  
 当你创建一种类型的对象派生自`COleDBRecordView`，调用的构造函数，以创建视图对象并标识该视图所基于的对话框资源之一。 按名称 （向构造函数传递一个字符串作为自变量） 或由其 ID (pass 作为自变量的无符号整数)，你可以标识资源。  
  
> [!NOTE]
>  在派生的类*必须*提供其自己的构造函数。 在构造函数中，调用构造函数中， `COleDBRecordView::COleDBRecordView`、 资源名称或 ID 为作为自变量。  
  
##  <a name="ongetrowset"></a>COleDBRecordView::OnGetRowset  
 返回的句柄**CRowset <>**与记录视图关联的对象。  
  
```  
virtual CRowset<>* OnGetRowset() = 0;  
 
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 你必须重写该成员函数以构造或中获取行集对象并返回到原来的句柄。 如果声明与 ClassWizard 记录视图类，向导会为你编写的默认重写。 ClassWizard 的默认实现返回存储在记录视图中，如果存在的行集句柄。 如果不是，构造类型的行集对象使用指定 ClassWizard 和调用其**打开**成员函数以打开该表或运行查询，然后返回该对象的句柄。  
  
> [!NOTE]
>  上一步 MFC 7.0`OnGetRowset`返回一个指向`CRowset`。 如果有调用的代码`OnGetRowset`，你需要返回类型更改为模板化类**CRowset <>**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]  
  
 有关详细信息和示例，请参阅文章[记录视图： 使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。  
  
##  <a name="onmove"></a>COleDBRecordView::OnMove  
 移动到另一条记录中的行集和显示其字段的记录控件中查看。  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>参数  
 `nIDMoveCommand`  
 以下标准命令 ID 值之一：  
  
- `ID_RECORD_FIRST`— 将移动到记录集的第一个记录。  
  
- `ID_RECORD_LAST`— 将移动到最后一个记录的记录集。  
  
- `ID_RECORD_NEXT`— 将移动到记录集的下一个记录。  
  
- `ID_RECORD_PREV`— 将移动到上一记录的记录集。  
  
### <a name="return-value"></a>返回值  
 如果移动已成功; 则为非 0如果移动请求被拒绝则否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现调用相应**移动**成员函数`CRowset`与记录视图关联的对象。  
  
 默认情况下，`OnMove`更新数据源上的当前记录，如果用户具有在记录视图中更改它。  
  
 应用程序向导会使用第一条记录、 最后一条记录下, 一条记录，以及上一条记录菜单项创建菜单资源。 如果选择可停靠工具栏选项，则应用程序向导还会使用按钮对应这些命令中创建工具栏。  
  
 如果移动记录集中的最后一条记录，记录视图将继续显示最后一条记录。 如果向后移过会将第一条记录，记录视图将继续显示第一条记录。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)



