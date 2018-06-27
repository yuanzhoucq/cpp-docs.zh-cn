---
title: CDaoRecordView 类 |Microsoft 文档
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
ms.openlocfilehash: a228a545061c4807688014b62907c4c41a82151e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952298"
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
|[CDaoRecordView::IsOnFirstRecord](#isonfirstrecord)|返回非零，如果当前记录是关联的记录集的第一个记录。|  
|[CDaoRecordView::IsOnLastRecord](#isonlastrecord)|返回非零，如果当前记录是在关联的记录集的最新记录。|  
|[CDaoRecordView::OnGetRecordset](#ongetrecordset)|返回指向派生自的类的对象的指针`CDaoRecordset`。 类向导为你重写此函数，并创建记录集，如有必要。|  
|[CDaoRecordView::OnMove](#onmove)|如果当前记录已更改，更新数据源，则将移动到指定的记录 （下一步、 上一个、 第一个或最后一个）。|  
  
## <a name="remarks"></a>备注  
 视图是直接连接到窗体视图`CDaoRecordset`对象。 该视图通过对话框模板资源创建和显示的字段`CDaoRecordset`对话框模板的控件中的对象。 `CDaoRecordView`对象使用对话框数据交换 (DDX) 和 DAO 记录字段交换 (DFX) 以自动进行的窗体上的控件和记录集的字段之间的数据移动。 `CDaoRecordView` 此外提供了一个默认实现来移动第一个下, 一步上, 一个或最后一个记录和用于更新当前在视图中的记录的接口。  
  
> [!NOTE]
>  DAO 数据库类有别于基于开放式数据库连接 (ODBC) 的 MFC 数据库类。 DAO 数据库类的所有名称都具有"CDao"前缀。 你仍可以访问 ODBC 数据源对于 DAO 类;DAO 类通常提供高级功能，因为它们使用 Microsoft Jet 数据库引擎。  
  
 创建记录视图的最常见方法是使用应用程序向导。 应用程序向导创建记录视图类和其关联的记录集类作为主干初学者应用程序的一部分。  
  
 如果你只需要单个窗体，则应用程序向导方法非常简便。 类向导允许你决定使用更高版本在开发过程中的记录视图。 如果你不使用应用程序向导创建记录视图类，你可以创建它更高版本与 ClassWizard。 使用 ClassWizard 单独创建记录视图和记录集并然后将其连接是最灵活的方法，因为它使您更好的控制命名记录集类和其。H /。CPP 文件。 此方法还可以有相同的记录集类上的多个记录视图。  
  
 若要使最终用户可在记录视图中移动在记录间容易，应用程序向导创建菜单 （或工具栏） 资源移动第一个下, 一步上, 一个或最后一个记录。 如果使用类向导创建记录视图类时，你需要这些资源自行创建具有菜单和位图编辑器。  
  
 有关移动到记录的默认实现的信息，请参阅`IsOnFirstRecord`和`IsOnLastRecord`和文章[使用记录视图](../../data/using-a-record-view-mfc-data-access.md)，这适用于`CRecordView`和`CDaoRecordView`。  
  
 `CDaoRecordView` 将跟踪的记录集内的用户的位置，以便记录视图可以更新用户界面。 当用户移动到记录集的任意一端时，记录视图禁用用户界面对象 — 如菜单项或工具栏按钮-移动进一步方向相同。  
  
 有关声明和使用记录视图和记录集类的详细信息，请参阅"设计和创建记录视图"中文章[记录视图](../../data/record-views-mfc-data-access.md)。 有关如何记录视图工作以及如何使用它们的详细信息，请参阅文章[使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。 两者都适用上面提到的所有文章`CRecordView`和`CDaoRecordView`。  
  
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
 当你创建一种类型的对象派生自`CDaoRecordView`，调用的构造函数初始化视图对象，并确定该视图所基于的对话框资源其中任一种形式。  
  
```  
explicit CDaoRecordView(LPCTSTR lpszTemplateName);  
explicit CDaoRecordView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>参数  
 *lpszTemplateName*  
 包含是对话框模板资源的名称的以 null 结尾的字符串。  
  
 *nIDTemplate*  
 包含对话框模板资源的 ID 号。  
  
### <a name="remarks"></a>备注  
 按名称 （向构造函数传递一个字符串作为自变量） 或由其 ID (pass 作为自变量的无符号整数)，或者可以确定资源。 使用的资源 ID 被建议。  
  
> [!NOTE]
>  在派生的类必须提供其自己的构造函数。 在派生类的构造函数调用的构造函数`CDaoRecordView::CDaoRecordView`资源名称或 ID 为作为自变量。  
  
 `CDaoRecordView::OnInitialUpdate` 调用`CWnd::UpdateData`，哪些调用`CWnd::DoDataExchange`。 此初始调用`DoDataExchange`连接`CDaoRecordView`（间接） 到控制`CDaoRecordset`字段 ClassWizard 所创建的数据成员。 这些数据成员不能直到后调用基类`CFormView::OnInitialUpdate`成员函数。  
  
> [!NOTE]
>  如果你使用 ClassWizard，向导将定义**枚举**值`CDaoRecordView::IDD`类声明并使用在成员初始化列表的构造函数。  
  
 [!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]  
  
##  <a name="isonfirstrecord"></a>  CDaoRecordView::IsOnFirstRecord  
 调用此成员函数可确定当前记录是否与此记录视图关联的记录集对象中的第一个记录。  
  
```  
BOOL IsOnFirstRecord();
```  
  
### <a name="return-value"></a>返回值  
 如果当前记录是记录集; 中的第一个记录则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数可用于编写您自己的实现的默认值由 ClassWizard 编写的命令更新处理程序。  
  
 如果用户移到第一条记录，任何用户界面对象 （如菜单项或工具栏按钮） framework 禁用则必须将移动到第一个或上一记录。  
  
##  <a name="isonlastrecord"></a>  CDaoRecordView::IsOnLastRecord  
 调用此成员函数可确定当前记录是否与此记录视图关联的记录集对象中的最后一个记录。  
  
```  
BOOL IsOnLastRecord();
```  
  
### <a name="return-value"></a>返回值  
 如果当前记录是记录集; 中的最后一个记录则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数可用于编写您自己的默认值的实现 ClassWizard 写入，以便移动在记录间支持用户界面的命令更新处理程序。  
  
> [!CAUTION]
>  此函数的结果是可靠的只不过该视图可能不能检测记录集的末尾，直到用户已移过它。 用户可能必须移动超出最后一条记录之前记录的视图可以判断它必须禁用将移动到下一个或最后一个记录任何用户界面对象。 如果用户移过最后一条记录，然后将移动返回到最后一个记录 （或在它之前），可以跟踪为记录集中的用户的位置记录视图并将其正确禁用用户界面对象。  
  
##  <a name="ongetrecordset"></a>  CDaoRecordView::OnGetRecordset  
 返回一个指向`CDaoRecordset`-派生与记录视图关联的对象。  
  
```  
virtual CDaoRecordset* OnGetRecordset() = 0;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针`CDaoRecordset`-派生对象，如果对象已成功创建; 否则为**NULL**指针。  
  
### <a name="remarks"></a>备注  
 你必须重写该成员函数以构造或获取记录集对象并返回指向它的指针。 如果声明与 ClassWizard 记录视图类，向导会为你编写的默认重写。 ClassWizard 的默认实现返回存储在记录视图中，如果存在的记录集指针。 如果不是，构造类型的记录集对象使用指定 ClassWizard 和调用其`Open`成员函数以打开该表或运行查询，然后将指针返回到对象。  
  
 有关详细信息和示例，请参阅文章[记录视图： 使用记录视图](../../data/using-a-record-view-mfc-data-access.md)。  
  
##  <a name="onmove"></a>  CDaoRecordView::OnMove  
 调用此成员函数以将移动到另一条记录的记录集的记录视图控件中显示其字段。  
  
```  
virtual BOOL OnMove(UINT nIDMoveCommand);
```  
  
### <a name="parameters"></a>参数  
 *nIDMoveCommand*  
 以下标准命令 ID 值之一：  
  
- `ID_RECORD_FIRST` 将移动到记录集的第一个记录。  
  
- `ID_RECORD_LAST` 在记录集中移动到最后一个记录。  
  
- `ID_RECORD_NEXT` 将移动到记录集的下一个记录。  
  
- `ID_RECORD_PREV` 将移动到上一记录的记录集。  
  
### <a name="return-value"></a>返回值  
 如果移动已成功; 则为非 0如果移动请求被拒绝则否则为 0。  
  
### <a name="remarks"></a>备注  
 默认实现调用相应的移动成员函数的`CDaoRecordset`与记录视图关联的对象。  
  
 默认情况下，`OnMove`更新数据源上的当前记录，如果用户具有在记录视图中更改它。  
  
 应用程序向导会使用第一条记录、 最后一条记录下, 一条记录，以及上一条记录菜单项创建菜单资源。 如果选择初始工具栏选项，则应用程序向导还会使用按钮对应这些命令中创建工具栏。  
  
 如果移动记录集中的最后一条记录，记录视图将继续显示最后一条记录。 如果向后移过会将第一条记录，记录视图将继续显示第一条记录。  
  
> [!CAUTION]
>  调用`OnMove`记录集是否没有记录，将引发异常。 调用相应的用户界面更新处理程序函数- `OnUpdateRecordFirst`， `OnUpdateRecordLast`， `OnUpdateRecordNext`，或`OnUpdateRecordPrev`-之前相对应移动操作，以确定记录集是否具有任何记录。  
  
## <a name="see-also"></a>请参阅  
 [CFormView 类](../../mfc/reference/cformview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset 类](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoTableDef 类](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoQueryDef 类](../../mfc/reference/cdaoquerydef-class.md)   
 [CDaoDatabase 类](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoWorkspace 类](../../mfc/reference/cdaoworkspace-class.md)   
 [CFormView 类](../../mfc/reference/cformview-class.md)
