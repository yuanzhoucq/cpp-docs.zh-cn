---
title: "CRecordView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
- AFXDB/CRecordView::OnMove
dev_langs:
- C++
helpviewer_keywords:
- CRecordView class
- ODBC recordsets, viewing records
- records, viewing ODBC
- views, ODBC
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
caps.latest.revision: 25
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
ms.openlocfilehash: 04ff47900037dcbaa12e2cba2c9a3e84caf54a69
ms.lasthandoff: 02/24/2017

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
|[CRecordView::CRecordView](#crecordview)|构造 `CRecordView` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CRecordView::IsOnFirstRecord](#isonfirstrecord)|返回非零，如果当前记录是在关联的记录集的第一个记录。|  
|[CRecordView::IsOnLastRecord](#isonlastrecord)|返回非零，如果当前记录是在关联的记录集的最后一个记录。|  
|[CRecordView::OnGetRecordset](#ongetrecordset)|返回指向派生类的对象的指针`CRecordset`。 类向导为您重写此函数和创建记录集，如有必要。|  
|[CRecordView::OnMove](#onmove)||  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CRecordView::OnMove](#onmove)|如果当前记录更改之后，在数据源中，对其进行更新，则会移到指定的记录 （下一步、 上一个、 第一个或上一次）。|  
  
## <a name="remarks"></a>备注  
 该视图是直接连接到窗体视图`CRecordset`对象。 该视图通过对话框模板资源创建和显示的字段`CRecordset`对话框模板的控件中的对象。 `CRecordView`对象使用对话框数据交换 (DDX) 和记录字段交换 (RFX) 以自动进行窗体控件和记录集字段之间的数据移动。 `CRecordView`此外提供了一个默认实现来移动到第一下, 一步上, 一个或最后一个记录和用于更新当前在视图上的记录的接口。  
  
> [!NOTE]
>  如果您正在使用的数据访问对象 (DAO) 类，而不是开放式数据库连接 (ODBC) 类，可以使用类[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)相反。 有关详细信息，请参阅文章[概述︰ 数据库编程](../../data/data-access-programming-mfc-atl.md)。  
  
 若要创建记录视图的最常见方法是使用应用程序向导。 Tge 应用程序向导创建记录视图类和其关联的记录集类作为主干初学者应用程序的一部分。 如果不使用应用程序向导创建记录视图类，您可以创建它更高版本与类向导。 如果您只需一个窗体，应用程序向导方法更为简单。 类向导允许您决定更高版本在开发过程中使用记录视图。 使用 ClassWizard 单独创建记录视图和记录集，然后连接它们是最灵活的方法，因为它使您更好的控制命名记录集类并将其。H /。CPP 文件。 此方法还使您可以有相同的记录集类上的多个记录视图。  
  
 为了方便最终用户可以从逐条移动记录视图中，应用程序向导创建菜单 （和 （可选） 工具栏） 用于移动资源到第一下, 一步上, 一个或最后一个记录。 如果使用类向导创建记录视图类，您需要这些资源自己创建具有菜单和位图编辑器。  
  
 有关移动到记录的默认实现的信息，请参阅`IsOnFirstRecord`和`IsOnLastRecord`和文章[使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。  
  
 `CRecordView`将跟踪的记录集内的用户的位置，以便记录视图可以更新用户界面。 当用户移动到记录集的任意一端时，记录视图禁用用户界面对象 — 如菜单项或工具栏按钮 — 移动进一步方向相同。  
  
 有关声明和使用记录视图和记录集类的详细信息，请参阅"设计和创建记录视图"中文章[记录视图](../../data/record-views-mfc-data-access.md)。 有关记录查看工作的方式以及如何使用它们的详细信息，请参阅文章[使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 `CRecordView`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdb.h  
  
##  <a name="crecordview"></a>CRecordView::CRecordView  
 当创建类型的对象派生自`CRecordView`，调用任一格式的构造函数，以便初始化视图的对象，并确定该视图所基于的对话框资源。  
  
```  
explicit CRecordView(LPCTSTR lpszTemplateName);  
explicit CRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>参数  
 `lpszTemplateName`  
 包含以 null 结尾的字符串，对话框模板资源的名称。  
  
 `nIDTemplate`  
 包含对话框模板资源的 ID 号。  
  
### <a name="remarks"></a>备注  
 按名称 (pass 字符串作为参数的构造函数) 或由其 ID (pass 作为参数的无符号整数)，或者可以确定该资源。 建议使用的资源 ID。  
  
> [!NOTE]
>  在派生的类*必须*提供其自己的构造函数。 在派生类的构造函数调用的构造函数`CRecordView::CRecordView`具有资源名称或 ID 作为参数，如下面的示例中所示。  
  
 **CRecordView::OnInitialUpdate**调用`UpdateData`，后者调用`DoDataExchange`。 此首次调用`DoDataExchange`连接`CRecordView`（间接） 为控制`CRecordset`字段数据成员创建的类向导。 在调用基类后这些数据成员不能使用直到**CFormView::OnInitialUpdate**成员函数。  
  
> [!NOTE]
>  如果您使用类向导，该向导定义`enum`值`CRecordView::IDD`，指定在类声明中，然后对于构造函数初始化成员列表中使用它。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDatabase #&32;](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]  
  
##  <a name="isonfirstrecord"></a>CRecordView::IsOnFirstRecord  
 调用此成员函数可确定当前记录是否与此记录视图关联的记录集对象中的第一个记录。  
  
```  
BOOL IsOnFirstRecord();
```  
  
### <a name="return-value"></a>返回值  
 如果当前记录是记录集; 中的第一个记录，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数可用于编写您自己的实现的默认命令更新处理程序编写的类向导。  
  
 如果用户移到第一个记录，该框架将禁用移动到第一个或上一条记录有任何用户界面对象。  
  
##  <a name="isonlastrecord"></a>CRecordView::IsOnLastRecord  
 调用此成员函数可确定当前记录是否与此记录视图关联的记录集对象中的最后一个记录。  
  
```  
BOOL IsOnLastRecord();
```  
  
### <a name="return-value"></a>返回值  
 如果当前记录是记录集; 中的最后一个记录，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数可用于编写您自己的实现的默认 ClassWizard 写入以支持用户界面，以迁移在记录间的命令更新处理程序。  
  
> [!CAUTION]
>  此函数的结果是可靠的只不过直到用户移过它，该视图无法检测到记录集的结尾。 记录视图可以告诉它必须禁用任何用户界面对象移动到下一个或最后一条记录之前，必须将用户移动超出了最后一条记录。 如果用户移过最后一条记录，然后移动回到最后一个记录 （或在它之前），记录视图可以跟踪为记录集中的用户的位置，并正确地禁用用户界面对象。 `IsOnLastRecord`在对实现函数的调用后也是不可靠**OnRecordLast**，哪些句柄`ID_RECORD_LAST`命令，或`CRecordset::MoveLast`。  
  
##  <a name="ongetrecordset"></a>CRecordView::OnGetRecordset  
 返回一个指向`CRecordset`-派生的记录视图与关联的对象。  
  
```  
virtual CRecordset* OnGetRecordset() = 0;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向`CRecordset`-派生对象，如果对象已成功创建; 否则为**NULL**指针。  
  
### <a name="remarks"></a>备注  
 必须重写该成员函数以构造或获取一个记录集对象并返回指向它的指针。 如果您声明与 ClassWizard 记录视图类，该向导为您编写的默认重写。 类向导的默认实现返回存储在记录视图中，如果存在一个记录集指针。 如果不是，将构造类型的记录集对象使用指定 ClassWizard 和调用其**打开**成员函数来打开表，或运行该查询，然后返回一个指向该对象。  
  
 有关详细信息和示例，请参阅文章[记录视图︰ 使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。  
  
##  <a name="onmove"></a>CRecordView::OnMove  
 调用此成员函数以将移动到另一条记录中的记录集中的记录视图控件中显示其字段。  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>参数  
 `nIDMoveCommand`  
 下面的标准命令 ID 值之一︰  
  
- `ID_RECORD_FIRST`将移动到记录集中的第一个记录。  
  
- `ID_RECORD_LAST`移动到最后一个记录集内的记录。  
  
- `ID_RECORD_NEXT`将移动到记录集的下一个记录。  
  
- `ID_RECORD_PREV`将移动到记录集的上一个记录。  
  
### <a name="return-value"></a>返回值  
 如果移动已成功，则非零值如果移动请求被拒绝，否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现调用相应**移动**成员函数`CRecordset`记录视图与关联的对象。  
  
 默认情况下，`OnMove`更新数据源上的当前记录，如果用户更改了它在记录视图中。  
  
 应用程序向导会使用第一条记录、 最后一条记录下, 一条记录，以及上一条记录菜单项创建的菜单资源。 如果选择可停靠工具栏选项，应用程序向导还用这些命令所对应的按钮创建工具栏。  
  
 如果您跳过在记录集中的最后一个记录，记录视图将继续显示最后一条记录。 如果您在第一条记录向后移动，记录视图仍将显示第一条记录。  
  
> [!CAUTION]
>  调用`OnMove`记录集含有没有记录的情况下将引发异常。 调用适当的用户界面更新处理程序函数- **OnUpdateRecordFirst**， **OnUpdateRecordLast**， **OnUpdateRecordNext**，或**OnUpdateRecordPrev** — 之前相对应移动运算来确定记录集是否具有任何记录。  
  
## <a name="see-also"></a>另请参阅  
 [CFormView 类](../../mfc/reference/cformview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRecordset 类](../../mfc/reference/crecordset-class.md)   
 [CFormView 类](../../mfc/reference/cformview-class.md)

