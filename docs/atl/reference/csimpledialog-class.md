---
title: CSimpleDialog 类
ms.date: 11/04/2016
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
ms.openlocfilehash: 345372d71ad96a74bb0ae6dd7e89bdf0724cd822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330822"
---
# <a name="csimpledialog-class"></a>CSimpleDialog 类

此类实现基本模式对话框。

## <a name="syntax"></a>语法

```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>
class CSimpleDialog : public CDialogImplBase
```

#### <a name="parameters"></a>参数

*t_wDlgTemplateID*

对话框模板资源的资源 ID。

*t_bCenter*<br/>
如果对话框对象要居于所有者窗口，则为 TRUE;如果对话框对象要位于所有者窗口上，则为 TRUE。否则 FALSE。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C简单对话：:Do模态](#domodal)|创建模式对话框。|

## <a name="remarks"></a>备注

实现具有基本功能的模式对话框。 `CSimpleDialog`仅支持 Windows 公共控件。 要创建和显示模态对话框，请创建此类的实例，为对话框提供现有资源模板的名称。 当用户单击具有预定义值（如 IDOK 或 IDCANCEL）的任何控件时，对话框对象将关闭。

`CSimpleDialog`允许您仅创建模式对话框。 `CSimpleDialog`提供对话框过程，该过程使用默认消息映射将消息定向到相应的处理程序。

有关详细信息[，请参阅实现对话框](../../atl/implementing-a-dialog-box.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CDialogImplBase`

`CSimpleDialog`

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="csimpledialogdomodal"></a><a name="domodal"></a>C简单对话：:Do模态

调用模态对话框，并在完成后返回对话框结果。

```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```

### <a name="parameters"></a>参数

*hWnd 父母*<br/>
对话框父级的句柄。 如果未提供任何值，则父级设置为当前活动窗口。

### <a name="return-value"></a>返回值

如果成功，返回值是取消对话框的控件的资源 ID。

如果函数失败，返回值为 -1。 若要获得扩展的错误信息，请调用 `GetLastError`。

### <a name="remarks"></a>备注

此方法处理与用户的所有交互，当对话框处于活动状态时。 这就是使对话框模态的原因;也就是说，在关闭对话框之前，用户无法与其他窗互。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
