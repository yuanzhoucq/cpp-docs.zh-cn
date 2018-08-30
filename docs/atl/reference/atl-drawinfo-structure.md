---
title: ATL_DRAWINFO 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
dev_langs:
- C++
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76f21f93bbd8386bbf0b4b63f3cf7c8b34057145
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210652"
---
# <a name="atldrawinfo-structure"></a>ATL_DRAWINFO 结构
包含用于呈现到各种目标，如打印机、 图元文件或 ActiveX 控件的信息。  
  
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
 `cbSize`  
 结构，以字节为单位的大小。  
  
 `dwDrawAspect`  
 指定目标的方式来表示。 表示可以包括内容、 图标、 缩略图或打印的文档。 有关可能的值的列表，请参阅[DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect)并[DVASPECT2](/windows/desktop/api/ocidl/ne-ocidl-tagdvaspect2)。  
  
 `lindex`  
 目标的绘制操作有关的值得关注的部分。 中的值而异其解释`dwDrawAspect`成员。  
  
 `ptd`  
 指向[DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice)启用绘制优化，具体取决于指定的方面的结构。 请注意，较新的对象和支持优化绘图接口的容器支持以及此成员。 较旧的对象和容器始终不支持优化绘图接口指定为空，此成员。  
  
 `hicTargetDev`  
 指向目标设备的信息上下文`ptd`对象可以从其提取设备量度并测试设备的功能。 如果`ptd`为 NULL，该对象应忽略中的值`hicTargetDev`成员。  
  
 `hdcDraw`  
 在其上绘制的设备上下文。 对于无窗口的对象，`hdcDraw`成员是在`MM_TEXT`其逻辑坐标为匹配包含窗口的工作区映射模式。 此外，设备上下文应处于相同状态通常通过传递一个`WM_PAINT`消息。  
  
 `prcBounds`  
 指向[RECTL](https://msdn.microsoft.com/library/windows/desktop/dd162907)结构，它在指定矩形`hdcDraw`和在绘制该对象。 此成员控制的定位和拉伸的对象。 此成员应为 NULL，以绘制无窗口的就地活动对象。 在每个其他情况下，NULL 不是合法的值，并应导致`E_INVALIDARG`错误代码。 如果该容器将非 NULL 值传递给无窗口对象，该对象应呈现到指定的设备上下文和矩形请求的方面。 容器应用程序可以请求从无窗口对象来呈现该对象的第二个、 非活动视图或打印对象。  
  
 `prcWBounds`  
 如果`hdcDraw`是图元文件设备上下文 (请参阅[GetDeviceCaps](/windows/desktop/api/wingdi/nf-wingdi-getdevicecaps) Windows SDK 中)，这是一个指向`RECTL`结构，它的基础元文件中指定的边框。 该矩形结构包含的窗口区和窗口来源。 这些值可用于绘制图元文件。 指示矩形`prcBounds`嵌套在此`prcWBounds`矩形; 它们处于相同的坐标空间。  
  
 `bOptimize`  
 如果该控件的绘图是经过优化，否则为 0，非零值。 在完成时，如果优化绘图，自动还原设备上下文的状态呈现。  
  
 `bZoomed`  
 如果目标具有的缩放因子，否则为 0，非零值。 在存储缩放系数`ZoomNum`。  
  
 `bRectInHimetric`  
 如果非零值的维度`prcBounds`中 HIMETRIC，否则为 0。  
  
 `ZoomNum`  
 宽度和在其中呈现的对象的矩形的高度。 沿 x 轴 （其当前范围内的对象的自然大小的比例） 目标的缩放系数是的值`ZoomNum.cx`的值除以`ZoomDen.cx`。 沿 y 轴的缩放系数是以类似的方式实现的。  
  
 `ZoomDen`  
 实际宽度和高度的目标。  
  
## <a name="remarks"></a>备注  
 此结构的典型用法是信息的检索的目标对象的呈现过程中。 例如，可以从检索的值 ATL_DRAWINFO 内你重载[CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)。  
  
 此结构可存储用于呈现外观的一个对象，用于在目标设备的相关信息。 提供的信息可在绘制到屏幕、 打印机或甚至图元文件。  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
## <a name="see-also"></a>请参阅  
  [类和结构](../../atl/reference/atl-classes.md) [iviewobject:: Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw)   
 [CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)





