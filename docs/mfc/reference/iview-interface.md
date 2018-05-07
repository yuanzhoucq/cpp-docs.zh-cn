---
title: IView 接口 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
dev_langs:
- C++
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a06243af3de7a2f4b32aa9a9ae492dfe3b2d3b64
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="iview-interface"></a>IView 接口
实现几种方法， [CWinFormsView](../../mfc/reference/cwinformsview-class.md)用于将视图通知发送到托管的控件。  
  
## <a name="syntax"></a>语法  
  
```  
interface class IView  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IView::OnActivateView](#onactivateview)|激活或停用视图时由 MFC 调用。|  
|[IView::OnInitialUpdate](#oninitialupdate)|视图首先附加到文档中之后, 但在最初显示的视图之前，由框架调用。|  
|[IView::OnUpdate](#onupdate)|修改视图的文档; 后，由 MFC 调用此函数允许更新以反映修改显示的视图。|  
  
## <a name="remarks"></a>备注  
 `IView` 实现几种方法，`CWinFormsView`用于转发到承载托管控件的常见视图通知。 这些是[OnInitialUpdate](#oninitialupdate)， [OnUpdate](#onupdate)和[OnActivateView](#onactivateview)。  
  
 `IView` 类似于[CView](../../mfc/reference/cview-class.md)，但仅用于托管的视图和控件。  
  
 有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  

## <a name="requirements"></a>要求  
 标头： afxwinforms.h （在程序集 atlmfc\lib\mfcmifc80.dll 中定义）  

## <a name="onactivateview"></a> IView::OnActivateView  
激活或停用视图时由 MFC 调用。
```
void OnActivateView(bool activate);
```
## <a name="parameters"></a>参数
`activate`  
指示是否视图处于激活或停用。  

## <a name="oninitialupdate"></a> IView::OnInitialUpdate
视图首先附加到文档中之后, 但在最初显示的视图之前，由框架调用。
```
void OnInitialUpdate();
```

## <a name="onupdate"></a> IView::OnUpdate 
由 MFC 视图的文档已被修改后调用。  
```
void OnUpdate();
```
## <a name="remarks"></a>备注  
此函数允许更新以反映修改显示的视图。

## <a name="see-also"></a>请参阅  
 [CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)   
 [CView 类](../../mfc/reference/cview-class.md)
