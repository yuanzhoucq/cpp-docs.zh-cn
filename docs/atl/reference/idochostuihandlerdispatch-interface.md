---
title: IDocHostUIHandlerDispatch 接口
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: b7072b80b738aa12635427a2604b38fb3585b452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329727"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch 接口

微软 HTML 解析和呈现引擎的接口。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

> [!NOTE]
> 下表中的链接指向[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))接口成员的 INet SDK 参考主题。 `IDocHostUIHandlerDispatch`具有与 的功能相同的`IDocUIHostHandler`功能，区别在于是异`IDocHostUIHandlerDispatch`接口，而`IDocUIHostHandler`是自定义接口。

|||
|-|-|
|[启用无模式](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|从[IOleInPlaceActiveObject](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)的 MSHTML 实现调用：：启用无模式 。 MSHTML 显示模式 UI 时也调用。|
|[筛选器数据对象](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|MSHTML 调用主机以允许主机替换 MSHTML 的数据对象。|
|[获取目标](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|MSHTML 调用时，它被用作放置目标，以允许主机提供替代[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)。|
|[获取外部](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|MSHTML 调用以获取主机的 IDispatch 接口。|
|[获取Hostinfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|检索 MSHTML 主机的 UI 功能。|
|[获取选项关键路径](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|返回 MSHTML 存储用户首选项的注册表项。|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|当 MSHTML 删除其菜单和工具栏时调用。|
|[OnDocWindow 激活](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|从[IOleInPlace 活动对象的](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)MSHTML 实现调用：onDocWindow激活 。|
|[在框架窗口激活](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|从[IOleInPlace 活动对象的](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)MSHTML 实现调用：在FrameWindow激活上。|
|[调整边框的大小](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|从[IOleInPlace 活动对象的](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)MSHTML 实现调用：调整边框 。|
|[显示上下文菜单](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|从 MSHTML 调用以显示上下文菜单。|
|[显示UI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|允许主机替换 MSHTML 菜单和工具栏。|
|[翻译加速器](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|当[IOleInPlace 活动对象：：翻译加速器](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator)或[IOleControlSite：：调用翻译加速器](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator)时，MSHTML 调用。|
|[翻译Url](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|MSHTML 调用以允许主机有机会修改要加载的 URL。|
|[更新 UI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|通知主机命令状态已更改。|

## <a name="remarks"></a>备注

主机可以通过实现此接口来替换 Microsoft HTML 解析和呈现引擎 （MSHTML） 使用的菜单、工具栏和上下文菜单。

## <a name="requirements"></a>要求

此接口的定义可作为 IDL 或C++，如下所示。

|定义类型|文件|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h （也包含在 ATLBase.h 中）|

## <a name="see-also"></a>另请参阅

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
