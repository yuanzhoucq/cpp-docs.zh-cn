---
title: "IView 接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IView
dev_langs:
- C++
helpviewer_keywords:
- views [MFC]
- IView class
- views, classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
caps.latest.revision: 23
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 9a8b5f2d9d123aa3032cb30ecdbdd1cd380b32f8
ms.lasthandoff: 02/24/2017

---
# <a name="iview-interface"></a>IView 接口
实现几种方法， [CWinFormsView](../../mfc/reference/cwinformsview-class.md)用于向托管控件发送查看通知。  
  
## <a name="syntax"></a>语法  
  
```  
interface class IView  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IView::OnActivateView](#onactivateview)|激活或停用视图时由 MFC 调用。|  
|[IView::OnInitialUpdate](#oninitialupdate)|查看第一次附加到文档之后, 但在最初显示的视图之前，由框架调用。|  
|[IView::OnUpdate](#onupdate)|后已修改该视图的文档，则由 MFC 调用使用此功能，要更新以反映修改其显示的视图。|  
  
## <a name="remarks"></a>备注  
 `IView`实现几种方法，`CWinFormsView`用于转发到承载的托管控件的常见查看通知。 这些是[OnInitialUpdate](#oninitialupdate)， [OnUpdate](#onupdate)和[OnActivateView](#onactivateview)。  
  
 `IView`类似于[CView](../../mfc/reference/cview-class.md)，但仅用于托管的视图和控件。  
  
 有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  

## <a name="requirements"></a>要求  
 标头︰ afxwinforms.h (在程序集 atlmfc\lib\mfcmifc80.dll 中定义)  

## <a name="a-nameonactivateviewa-iviewonactivateview"></a><a name="onactivateview"></a>IView::OnActivateView  
激活或停用视图时由 MFC 调用。
```
void OnActivateView(bool activate);
```
## <a name="parameters"></a>参数
`activate`  
指示是否视图处于激活还是停用状态。  

## <a name="a-nameoninitialupdatea-iviewoninitialupdate"></a><a name="oninitialupdate"></a>IView::OnInitialUpdate
查看第一次附加到文档之后, 但在最初显示的视图之前，由框架调用。
```
void OnInitialUpdate();
```

## <a name="a-nameonupdatea-iviewonupdate"></a><a name="onupdate"></a>IView::OnUpdate 
由 MFC 视图的文档，修改后调用。  
```
void OnUpdate();
```
## <a name="remarks"></a>备注  
使用此功能，要更新以反映修改其显示的视图。

## <a name="see-also"></a>另请参阅  
 [CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)   
 [CView 类](../../mfc/reference/cview-class.md)

