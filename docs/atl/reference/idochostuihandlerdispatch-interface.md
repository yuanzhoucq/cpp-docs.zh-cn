---
title: IDocHostUIHandlerDispatch 接口
ms.date: 11/04/2016
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: 5bf405f66bdef54f354f9e6c230207d2933ee352
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483624"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch 接口

Microsoft HTML 分析和呈现引擎的接口。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

> [!NOTE]
>  下表中的链接将指向的成员的 INet SDK 参考主题[IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)接口。 `IDocHostUIHandlerDispatch` 具有相同的功能`IDocUIHostHandler`，使用不同的是，`IDocHostUIHandlerDispatch`是调度接口，而`IDocUIHostHandler`是自定义的接口。

|||
|-|-|
|[EnableModeless](https://msdn.microsoft.com/library/aa753253.aspx)|从 MSHTML 实现调用[IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)。 也称为 MSHTML 显示模式 UI 时。|
|[FilterDataObject](https://msdn.microsoft.com/library/aa753254.aspx)|调用由 MSHTML 以允许主机替换 MSHTML 的数据对象在主机上。|
|[GetDropTarget](https://msdn.microsoft.com/library/aa753255.aspx)|当它被用作拖放目标以允许主机提供替代时，调用 MSHTML [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)。|
|[GetExternal](https://msdn.microsoft.com/library/aa753256.aspx)|由 MSHTML 获取主机的 IDispatch 接口调用。|
|[GetHostInfo](https://msdn.microsoft.com/library/aa753257.aspx)|检索 MSHTML 主机的用户界面功能。|
|[GetOptionKeyPath](https://msdn.microsoft.com/library/aa753258.aspx)|返回 MSHTML 在其下存储用户首选项的注册表项。|
|[HideUI](https://msdn.microsoft.com/library/aa753259.aspx)|当 MSHTML 删除其菜单和工具栏时调用。|
|[OnDocWindowActivate](https://msdn.microsoft.com/library/aa753261.aspx)|从 MSHTML 实现调用[IOleInPlaceActiveObject::OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)。|
|[OnFrameWindowActivate](https://msdn.microsoft.com/library/aa753262.aspx)|从 MSHTML 实现调用[ioleinplaceactiveobject:: Onframewindowactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)。|
|[ResizeBorder](https://msdn.microsoft.com/library/aa753263.aspx)|从 MSHTML 实现调用[IOleInPlaceActiveObject::ResizeBorder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)。|
|[ShowContextMenu](https://msdn.microsoft.com/library/aa753264.aspx)|从 MSHTML 以显示上下文菜单调用。|
|[ShowUI](https://msdn.microsoft.com/library/aa753265.aspx)|允许主机替换 MSHTML 菜单和工具栏。|
|[TranslateAccelerator](https://msdn.microsoft.com/library/aa753266.aspx)|由 MSHTML 调用时[:: Translateaccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator)或[iolecontrolsite:: Translateaccelerator](/windows/desktop/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator)调用。|
|[TranslateUrl](https://msdn.microsoft.com/library/aa753267.aspx)|由 MSHTML 以允许主机有机会修改要加载的 URL 调用。|
|[UpdateUI](https://msdn.microsoft.com/library/aa753268.aspx)|通知主机命令状态已更改。|

## <a name="remarks"></a>备注

主机可以替换菜单、 工具栏和上下文菜单通过实现此接口由 Microsoft HTML 分析和呈现引擎 (MSHTML)。

## <a name="requirements"></a>要求

此接口的定义现在以 IDL 或 c + +，如下所示。

|定义类型|文件|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h （也包括在 ATLBase.h）|

## <a name="see-also"></a>请参阅

[IDocUIHostHandler](https://msdn.microsoft.com/library/aa753260.aspx)

