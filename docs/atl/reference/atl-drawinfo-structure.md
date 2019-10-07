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
ms.openlocfilehash: 728a7eed418a6600c9247b91ff7b777dd458e621
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498011"
---
# <a name="atl_drawinfo-structure"></a>ATL_DRAWINFO 结构

包含用于呈现到各种目标 (如打印机、图元文件或 ActiveX 控件) 的信息。

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
结构的大小 (以字节为单位)。

`dwDrawAspect`<br/>
指定如何表示目标。 表示形式可以包括内容、图标、缩略图或打印文档。 有关可能值的列表, 请参阅[DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)和[DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2)。

`lindex`<br/>
绘图操作所需的目标部分。 根据`dwDrawAspect`成员的值, 它的解释会有所不同。

`ptd`<br/>
指向[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)结构的指针, 该结构根据指定的方位启用绘制优化。 请注意, 支持优化的绘图接口的较新对象和容器也支持此成员。 不支持优化的绘图接口的较旧对象和容器始终为此成员指定 NULL。

`hicTargetDev`<br/>
目标设备`ptd`的信息上下文, 对象可从中提取设备度量值并测试设备的功能。 如果`ptd`为 NULL, 则对象应忽略`hicTargetDev`成员中的值。

`hdcDraw`<br/>
要在其上进行绘制的设备上下文。 对于无窗口对象, `hdcDraw`成员处于`MM_TEXT`映射模式, 其逻辑坐标与包含窗口的工作区坐标匹配。 此外, 设备上下文应该与通常通过`WM_PAINT`消息传递的上下文处于相同的状态。

`prcBounds`<br/>
指向[RECTL](/previous-versions//dd162907\(v=vs.85\))结构的指针, 该结构指定`hdcDraw`在其上绘制对象的和中的矩形。 此成员控制对象的定位和拉伸。 此成员应为空以绘制无窗口就地活动对象。 在其他所有情况下, NULL 不是合法值并且应该导致`E_INVALIDARG`错误代码。 如果容器将非 NULL 值传递到无窗口对象, 则该对象应将所请求的内容呈现到指定的设备上下文和矩形。 容器可以从无窗口对象请求此项, 以呈现对象的第二个非活动视图或打印对象。

`prcWBounds`<br/>
如果`hdcDraw`是图元文件设备上下文 (请参阅 Windows SDK 中的[GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) ), 这是指向`RECTL`结构的指针, 该结构指定基础图元文件中的边框。 矩形结构包含窗口范围和窗口源。 这些值可用于绘制图元文件。 指示的`prcBounds`矩形嵌套在此`prcWBounds`矩形内; 它们位于同一坐标空间中。

`bOptimize`<br/>
如果要优化控件的绘制, 则为非零; 否则为0。 如果绘图经过优化, 则在完成呈现后, 会自动还原设备上下文的状态。

`bZoomed`<br/>
如果目标具有缩放系数, 则为非零; 否则为0。 缩放系数存储在中`ZoomNum`。

`bRectInHimetric`<br/>
如果的维度`prcBounds`在 HIMETRIC 中, 则为非零; 否则为0。

`ZoomNum`<br/>
呈现对象的矩形的宽度和高度。 在 x 轴上沿 x 轴 (对象的自然大小到其当前范围的比例) 的缩放因子是`ZoomNum.cx`除以`ZoomDen.cx`值的值。 沿 y 轴的缩放系数的实现方式类似。

`ZoomDen`<br/>
目标的实际宽度和高度。

## <a name="remarks"></a>备注

此结构的典型用法是在呈现目标对象的过程中检索信息。 例如, 可以从[CComControlBase:: OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)的重载内的 ATL_DRAWINFO 中检索值。

此结构存储用于呈现目标设备的对象外观的相关信息。 提供的信息可用于绘制到屏幕、打印机甚至图元文件。

## <a name="requirements"></a>要求

**标头:** atlctl

## <a name="see-also"></a>请参阅

[类和结构](../../atl/reference/atl-classes.md)<br/>
[IViewObject::Draw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
