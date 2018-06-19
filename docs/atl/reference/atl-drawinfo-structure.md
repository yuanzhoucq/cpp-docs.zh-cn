---
title: ATL_DRAWINFO 结构 |Microsoft 文档
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
ms.openlocfilehash: 6c8ba7be259a10ee1bf47bbdc401a2389adac2be
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255959"
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
  
 **dwDrawAspect**  
 指定目标的表示方式。 表示形式可以包括内容、 图标、 一个缩略图或打印的文档。 有关可能的值的列表，请参阅[DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)和[DVASPECT2](http://msdn.microsoft.com/library/windows/desktop/ms688644)。  
  
 **lindex**  
 目标的是与绘制操作有关的感兴趣的部分。 中的值而异其解释**dwDrawAspect**成员。  
  
 **ptd**  
 指向[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)启用绘制优化，具体取决于指定的方面的结构。 请注意，较新的对象和容器支持优化绘制接口的支持以及此成员。 较旧的对象和容器始终不支持优化绘制接口指定**NULL**有关此成员。  
  
 **hicTargetDev**  
 指向目标设备的信息上下文**ptd**对象可以从中提取设备量度并测试设备的功能。 如果**ptd**是**NULL**，该对象应忽略中的值**hicTargetDev**成员。  
  
 **hdcDraw**  
 在其上绘制设备上下文。 对于无窗口对象， **hdcDraw**成员处于`MM_TEXT`映射模式匹配包含窗口的客户端坐标其逻辑坐标。 此外，设备上下文应处于同一状态与通常通过传递`WM_PAINT`消息。  
  
 **prcBounds**  
 指向[RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907)结构，它在指定矩形**hdcDraw**和在绘制对象。 此成员控制的位置和延伸的对象。 此成员应为**NULL**绘制无窗口处于就地活动对象。 在每个其他情况下， **NULL**不是合法的值和应导致`E_INVALIDARG`错误代码。 如果容器通过非**NULL**无窗口对象，该对象的值应呈现到指定的设备上下文和矩形的请求的方面。 容器应用程序可以请求从无窗口对象来呈现该对象的第二个、 非活动视图，或打印对象。  
  
 **prcWBounds**  
 如果**hdcDraw**是图元文件设备上下文 (请参阅[GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877) Windows SDK 中)，这是一个指向**RECTL**结构，它指定中的绑定矩形基础的图元文件。 矩形结构包含的窗口范围和窗口来源。 这些值可用于绘制图元文件。 矩形由**prcBounds**嵌套在这**prcWBounds**矩形; 它们处于相同的坐标空间。  
  
 **bOptimize**  
 如果控件的绘制既要进行了优化，否则为 0，则为非 0。 如果绘图进行了优化，在完成时，设备上下文的状态会自动还原呈现。  
  
 **bZoomed**  
 如果目标不包含缩放系数，否则为 0，则为非 0。 缩放系数存储在**ZoomNum**。  
  
 **bRectInHimetric**  
 如果非零的尺寸**prcBounds**中**HIMETRIC**，否则为 0。  
  
 **ZoomNum**  
 宽度和该对象将呈现到其中的矩形的高度。 缩放系数沿 x 轴 （其当前范围内的对象的原始大小的比例） 的目标是值**ZoomNum.cx**除以的值**ZoomDen.cx**。 沿 y 轴缩放系数是以类似的方式实现的。  
  
 **ZoomDen**  
 实际宽度和高度的目标。  
  
## <a name="remarks"></a>备注  
 此结构的典型用法是信息的检索在呈现目标对象的过程。 例如，无法检索值从`ATL_DRAWINFO`内你重载[CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)。  
  
 此结构存储用于呈现目标设备的对象的外观的相关信息。 提供的信息可在屏幕、 打印机，或甚至图元文件绘制。  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
## <a name="see-also"></a>请参阅  
  [类和结构](../../atl/reference/atl-classes.md) [iviewobject:: Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)   
 [CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)





