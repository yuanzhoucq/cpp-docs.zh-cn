---
title: IView 接口
ms.date: 11/04/2016
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
ms.openlocfilehash: 22e08a70ff4cc742406a1489899c0ba1df7eb664
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267818"
---
# <a name="iview-interface"></a>IView 接口

实现几种方法的[CWinFormsView](../../mfc/reference/cwinformsview-class.md)用于将查看通知发送到的托管控件。

## <a name="syntax"></a>语法

```
interface class IView
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IView::OnActivateView](#onactivateview)|由 MFC 激活或停用视图时调用。|
|[IView::OnInitialUpdate](#oninitialupdate)|该视图首次附加到文档中之后, 但在最初显示的视图之前由框架调用。|
|[IView::OnUpdate](#onupdate)|后已修改，视图的文档，则由 MFC 调用使用此功能，要更新其显示效果以反映修改的视图。|

## <a name="remarks"></a>备注

`IView` 实现几种方法的`CWinFormsView`使用将转发到承载托管控件的常见查看通知。 这些是[OnInitialUpdate](#oninitialupdate)， [OnUpdate](#onupdate)并[OnActivateView](#onactivateview)。

`IView` 类似于[CView](../../mfc/reference/cview-class.md)，但只能用于托管的视图和控件。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="requirements"></a>要求

标头： afxwinforms.h （在程序集 atlmfc\lib\mfcmifc80.dll 中定义）

## <a name="onactivateview"></a> IView::OnActivateView

由 MFC 激活或停用视图时调用。
```
void OnActivateView(bool activate);
```

## <a name="parameters"></a>参数

*activate*<br/>
指示是否视图处于激活或停用。

## <a name="oninitialupdate"></a> IView::OnInitialUpdate

该视图首次附加到文档中之后, 但在最初显示的视图之前由框架调用。
```
void OnInitialUpdate();
```

## <a name="onupdate"></a> IView::OnUpdate

由 MFC 视图的文档已被修改后调用。
```
void OnUpdate();
```

## <a name="remarks"></a>备注

使用此功能，要更新其显示效果以反映修改的视图。

## <a name="see-also"></a>请参阅

[CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)
