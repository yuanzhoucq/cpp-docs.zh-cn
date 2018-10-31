---
title: ICommandTarget 接口 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
dev_langs:
- C++
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee8a4bb3f80d9776aec4fd7a6af0d1523c60064d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066079"
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

