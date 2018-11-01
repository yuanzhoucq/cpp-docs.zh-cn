---
title: ICommandTarget 接口
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: 830802f960cba1789c21c53efbf0ed05de3ac4cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557447"
---
# <a name="icommandtarget-interface"></a>ICommandTarget 接口

使用接口来接收来自命令源对象的命令提供了一个用户控件。

## <a name="syntax"></a>语法

```
interface class ICommandTarget
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[ICommandTarget::Initialize](#initialize)|初始化命令目标对象。|

## <a name="remarks"></a>备注

当您承载在 MFC 视图中，用户控件时[CWinFormsView](../../mfc/reference/cwinformsview-class.md)路由命令和更新命令 UI 消息到用户控件，使其能够处理 MFC 命令 （例如，框架菜单项和工具栏按钮）。 通过实现`ICommandTarget`，让用户能够控制对引用[ICommandSource](../../mfc/reference/icommandsource-interface.md)对象。

请参阅[如何： 向 Windows 窗体控件添加命令传送](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)以举例说明如何使用`ICommandTarget`。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="requirements"></a>要求

**标头：** afxwinforms.h （在程序集 atlmfc\lib\mfcmifc80.dll 中定义）

##  <a name="initialize"></a> ICommandTarget::Initialize

初始化命令目标对象。

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>参数

*cmdSource*<br/>
命令源对象的句柄。

### <a name="remarks"></a>备注

托管时 MFC 视图中的用户控件，CWinFormsView 将命令和更新命令 UI 消息路由到用户控件，使其能够处理 MFC 命令。

此方法初始化命令目标对象，并将其与指定的命令源对象 cmdSource 关联。 用户控件类实现中，应调用它。 在初始化时，应该向命令源对象通过调用在初始化实现 ICommandSource::AddCommandHandler 注册命令处理程序。 请参阅如何： 将命令路由添加到 Windows 窗体控件中举例说明如何使用初始化执行此操作。

## <a name="see-also"></a>请参阅

[如何：向 Windows 窗体控件添加命令传送](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource 接口](../../mfc/reference/icommandsource-interface.md)

