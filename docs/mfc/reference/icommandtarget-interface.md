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
ms.openlocfilehash: 865a8a27d96f84f536e40ec5a7bbbbdd9837dfcd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356915"
---
# <a name="icommandtarget-interface"></a>ICommandTarget 接口

为用户提供具有从命令源对象接收命令的接口。

## <a name="syntax"></a>语法

```
interface class ICommandTarget
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[ICommand 目标：：初始化](#initialize)|初始化命令目标对象。|

## <a name="remarks"></a>备注

当您在 MFC 视图中托管用户控件时[，CWinFormsView](../../mfc/reference/cwinformsview-class.md)会将命令和命令 UI 消息更新到用户控件，以允许它处理 MFC 命令（例如，框架菜单项和工具栏按钮）。 通过实现`ICommandTarget`，向用户控件提供对[ICommandSource](../../mfc/reference/icommandsource-interface.md)对象的引用。

有关如何使用，请参阅[：将命令路由添加到 Windows 窗体控件](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)`ICommandTarget`。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="requirements"></a>要求

**标题**：afxwinforms.h（在程序集 atlmfc_lib_mfcmc80.dll 中定义）

## <a name="icommandtargetinitialize"></a><a name="initialize"></a>ICommand 目标：：初始化

初始化命令目标对象。

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>参数

*cmd来源*<br/>
命令源对象的句柄。

### <a name="remarks"></a>备注

当您在 MFC 视图中托管用户控件时，CWinFormsView 会将命令和命令 UI 消息更新到用户控件以允许它处理 MFC 命令。

此方法初始化命令目标对象并将其与指定的命令源对象 cmdSource 关联。 应在用户控件类实现中调用它。 在初始化时，应通过在初始化实现中调用 ICommandSource：：addCommandHandler，将命令处理程序与命令源对象注册。 有关如何将命令路由添加到 Windows 窗体控件，请参阅如何使用初始化执行此操作的示例。

## <a name="see-also"></a>另请参阅

[如何：向 Windows 窗体控件添加命令传送](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource 接口](../../mfc/reference/icommandsource-interface.md)
