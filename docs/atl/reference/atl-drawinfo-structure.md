---
title: ATL_DRAWINFO 结构
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: fb50f49d387e8620f3d5bbb41263738adbd8b437
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748801"
---
# <a name="atl_drawinfo-structure"></a>ATL_DRAWINFO 结构

包含用于呈现到各种目标（如打印机、元文件或 ActiveX 控件）的信息。

## <a name="syntax"></a>语法

```
struct ATL_DRAWINFO {
    UINT cbSize;
    DWORD dwDrawAspect;
    LONG lindex;
    DVTARGETDEVICE* ptd;
    HDC hicTargetDev;
    HDC hdcDraw;
    LPCRECTL prcBounds;
    LPCRECTL prcWBounds;
    BOOL bOptimize;
    BOOL bZoomed;
    BOOL bRectInHimetric;
    SIZEL ZoomNum;
    SIZEL ZoomDen;
};
```

## <a name="members"></a>成员

`cbSize`<br/>
结构的大小（以字节为单位）。

`dwDrawAspect`<br/>
指定如何表示目标。 表示可以包括内容、图标、缩略图或打印的文档。 有关可能值的列表，请参阅[DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)和[DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2)。

`lindex`<br/>
对绘制操作感兴趣的目标部分。 其解释因`dwDrawAspect`成员中的值而异。

`ptd`<br/>
指向[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)结构的指针，该结构可根据指定的方面进行绘制优化。 请注意，支持优化绘图接口的较新的对象和容器也支持此成员。 不支持优化绘图接口的旧对象和容器始终为此成员指定 NULL。

`hicTargetDev`<br/>
指向的目标设备的信息上下文，对象可以从中`ptd`提取设备指标并测试设备的功能。 如果`ptd`为 NULL，则对象应忽略成员中`hicTargetDev`的值。

`hdcDraw`<br/>
要绘制的设备上下文。 对于无窗口对象，`hdcDraw`成员处于`MM_TEXT`映射模式，其逻辑坐标与包含窗口的客户端坐标匹配。 此外，设备上下文应处于与通常通过`WM_PAINT`消息传递的状态相同的状态。

`prcBounds`<br/>
指向[RECTL](/windows/win32/api/windef/ns-windef-rectl)结构的指针，指定`hdcDraw`在上和其中绘制对象的矩形。 此成员控制对象的定位和拉伸。 此成员应为 NULL，以绘制无窗口就地活动对象。 在所有其他情况下，NULL 不是法律价值，应会导致`E_INVALIDARG`错误代码。 如果容器将非 NULL 值传递给无窗口对象，则该对象应将请求的方面呈现为指定的设备上下文和矩形。 容器可以从无窗口对象请求此视图以呈现对象的第二个非活动视图或打印该对象。

`prcWBounds`<br/>
如果是`hdcDraw`元文件设备上下文（请参阅 Windows SDK 中的[GetDeviceCaps），](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps)则这是指向在基础`RECTL`元文件中指定边界矩形的结构的指针。 矩形结构包含窗口范围和窗口原点。 这些值可用于绘制元文件。 表示的矩形嵌套`prcBounds`在此矩形内;如果`prcWBounds`位于 此矩形内，则表示的矩形位于此矩形内。它们位于同一坐标空间中。

`bOptimize`<br/>
如果要优化控件的图形，则非零，否则为 0。 如果绘图已优化，则完成渲染后，将自动还原设备上下文的状态。

`bZoomed`<br/>
如果目标具有缩放系数，则非零，否则为 0。 缩放系数存储在 中`ZoomNum`。

`bRectInHimetric`<br/>
如果的`prcBounds`尺寸在 HIMETRIC 中，则非零，否则为 0。

`ZoomNum`<br/>
对象呈现到的矩形的宽度和高度。 沿目标的 x 轴（对象的自然大小与其当前范围的比例）的缩放系数是`ZoomNum.cx`除以 的值。 `ZoomDen.cx` 沿 y 轴的缩放系数以类似方式实现。

`ZoomDen`<br/>
目标的实际宽度和高度。

## <a name="remarks"></a>备注

此结构的典型用法是在呈现目标对象期间检索信息。 例如，可以从 CcomControlBase 的重载中从ATL_DRAWINFO检索值[：onDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)。

此结构存储用于呈现目标设备对象外观的相关信息。 提供的信息可用于绘制到屏幕、打印机甚至元文件。

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="see-also"></a>请参阅

[类和结构](../../atl/reference/atl-classes.md)<br/>
[IView对象：:D原始](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase：OnDraw高级](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
