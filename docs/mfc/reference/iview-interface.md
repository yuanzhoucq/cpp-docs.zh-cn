---
title: IView 界面
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
ms.openlocfilehash: dfe77699a51ad2670c703d02e13e9062e76debcd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751280"
---
# <a name="iview-interface"></a>IView 界面

实现[CWinFormsView](../../mfc/reference/cwinformsview-class.md)用于向托管控件发送视图通知的几种方法。

## <a name="syntax"></a>语法

```
interface class IView
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IView：打开激活视图](#onactivateview)|当视图激活或停用时，MFC 调用。|
|[IView：：初始更新](#oninitialupdate)|视图首次附加到文档后由框架调用，但在最初显示视图之前。|
|[IView：：更新](#onupdate)|修改视图文档后由 MFC 调用;此功能允许视图更新其显示以反映修改。|

## <a name="remarks"></a>备注

`IView`实现几种方法，`CWinFormsView`用于将公共视图通知转发到托管托管控件。 这些是["初始更新](#oninitialupdate)["、"更新"](#onupdate)和["激活视图](#onactivateview)"。

`IView`与[CView](../../mfc/reference/cview-class.md)类似，但仅用于托管视图和控件。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="requirements"></a>要求

标头：afxwinforms.h（在程序集 atlmfc\lib\mfcmifc80.dll 中定义）

## <a name="iviewonactivateview"></a><a name="onactivateview"></a>IView：打开激活视图

当视图激活或停用时，MFC 调用。

```cpp
void OnActivateView(bool activate);
```

## <a name="parameters"></a>参数

*激活*<br/>
指示视图是正在激活还是停用。

## <a name="iviewoninitialupdate"></a><a name="oninitialupdate"></a>IView：：初始更新

视图首次附加到文档后由框架调用，但在最初显示视图之前。

```cpp
void OnInitialUpdate();
```

## <a name="iviewonupdate"></a><a name="onupdate"></a>IView：：更新

修改视图文档后由 MFC 调用。

```cpp
void OnUpdate();
```

## <a name="remarks"></a>备注

此功能允许视图更新其显示以反映修改。

## <a name="see-also"></a>请参阅

[CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)
