---
title: "COleDBRecordView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDBRecordView
dev_langs:
- C++
helpviewer_keywords:
- MFC, OLE DB
- COleDBRecordView class
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 89b5cb175900d11854dcad03440a1ef0bfb8cff9
ms.lasthandoff: 02/24/2017

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
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|构造 `COleDBRecordView` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleDBRecordView::OnGetRowset](#ongetrowset)|返回一个标准`HRESULT`值。|  
|[COleDBRecordView::OnMove](#onmove)|在数据源上更新的当前记录 （如果更新），然后移动到指定的记录 （下一步、 上一个、 第一个或上一次）。|  
  
## <a name="remarks"></a>备注  
 该视图是直接连接到窗体视图`CRowset`对象。 该视图通过对话框模板资源创建和显示的字段`CRowset`对话框模板的控件中的对象。 `COleDBRecordView`对象使用对话框数据交换 (DDX)，并导航功能内置于`CRowset`，以自动进行窗体控件和行集的字段之间的数据移动。 `COleDBRecordView`此外提供了一个默认实现来移动到第一下, 一步上, 一个或最后一个记录和用于更新当前在视图上的记录的接口。  
  
 您可以使用与 DDX 函数**COleDbRecordView**以直接从数据库记录集获取数据并将其显示在对话框控件。 应使用**DDX_\* **方法 (如`DDX_Text`)，而不**DDX_Field\* **函数 (如`DDX_FieldText`) 与**COleDbRecordView**。 `DDX_FieldText`不会使用**COleDbRecordView**因为`DDX_FieldText`采用类型的其他参数**CRecordset\* ** (对于`CRecordView`) 或**CDaoRecordset\* ** (对于`CDaoRecordView`)。  
  
> [!NOTE]
>  如果您正在使用数据访问对象 (DAO) 类，而不是 OLE DB 使用者模板类，可以使用类[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)相反。 有关详细信息，请参阅文章[概述︰ 数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 `COleDBRecordView`将跟踪的用户的位置的行集中，以便记录视图可以更新用户界面。 当用户移到行集中的任意一端时，记录视图禁用用户界面对象 â €"如菜单项或工具栏按钮 â €"用于移动进一步方向相同。  
  
 有关行集类的详细信息，请参阅[使用 OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)文章。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `COleDBRecordView`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxoledb.h  
  
##  <a name="a-namecoledbrecordviewa--coledbrecordviewcoledbrecordview"></a><a name="coledbrecordview"></a>COleDBRecordView::COleDBRecordView  
 构造 `COleDBRecordView` 对象。  
  
```  
COleDBRecordView(LPCTSTR lpszTemplateName);  
COleDBRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>参数  
 `lpszTemplateName`  
 包含以 null 结尾的字符串是对话框模板资源的名称。  
  
 `nIDTemplate`  
 包含对话框模板资源的 ID 号。  
  
### <a name="remarks"></a>备注  
 当创建类型的对象派生自`COleDBRecordView`，调用的构造函数来创建视图对象并标识该视图所基于的对话框资源之一。 按名称 (pass 字符串作为参数的构造函数) 或由其 ID (pass 作为参数的无符号整数)，您可以标识该资源。  
  
> [!NOTE]
>  在派生的类*必须*提供其自己的构造函数。 在构造函数中，调用构造函数中， `COleDBRecordView::COleDBRecordView`、 具有资源名称或 ID 作为参数。  
  
##  <a name="a-nameongetrowseta--coledbrecordviewongetrowset"></a><a name="ongetrowset"></a>COleDBRecordView::OnGetRowset  
 返回的句柄**CRowset<> </> **记录视图与关联的对象。  
  
```  
virtual CRowset<>* OnGetRowset(Â) = 0;  
 
```  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
### <a name="remarks"></a>备注  
 必须重写该成员函数以构造或获取行集对象并返回一个句柄。 如果您声明与 ClassWizard 记录视图类，该向导为您编写的默认重写。 类向导的默认实现返回存储在记录视图中，如果存在的行集句柄。 如果它不是，构造类型的行集对象使用指定 ClassWizard 和调用其**打开**成员函数来打开表，或运行该查询，然后返回该对象的句柄。  
  
> [!NOTE]
>  上一步 MFC 7.0`OnGetRowset`返回一个指向`CRowset`。 如果您的代码调用`OnGetRowset`，您需要将返回类型更改为模板类**CRowset<>**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase #&38;](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]  
  
 有关详细信息和示例，请参阅文章[记录视图︰ 使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。  
  
##  <a name="a-nameonmovea--coledbrecordviewonmove"></a><a name="onmove"></a>COleDBRecordView::OnMove  
 转到另一条记录中的行集和显示其字段在控件中的记录的视图。  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>参数  
 `nIDMoveCommand`  
 下面的标准命令 ID 值之一︰  
  
- `ID_RECORD_FIRST`Â Â Â 将移动到记录集中的第一个记录。  
  
- `ID_RECORD_LAST`Â Â Â 将在记录集中记录移到最后一个。  
  
- `ID_RECORD_NEXT`Â Â Â 将移动到记录集的下一个记录。  
  
- `ID_RECORD_PREV`Â Â Â 将移动到记录集的上一个记录。  
  
### <a name="return-value"></a>返回值  
 如果移动已成功，则非零值如果移动请求被拒绝，否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现调用相应**移动**成员函数`CRowset`记录视图与关联的对象。  
  
 默认情况下，`OnMove`更新数据源上的当前记录，如果用户具有在记录视图中更改它。  
  
 应用程序向导会使用第一条记录、 最后一条记录下, 一条记录，以及上一条记录菜单项创建的菜单资源。 如果选择可停靠工具栏选项，应用程序向导还用这些命令所对应的按钮创建工具栏。  
  
 如果您跳过在记录集中的最后一个记录，记录视图将继续显示最后一条记录。 如果您在第一条记录向后移动，记录视图仍将显示第一条记录。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)




