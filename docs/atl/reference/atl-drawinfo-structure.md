---
title: "ATL_DRAWINFO 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
dev_langs:
- C++
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: bc124de97acf85d6e706605afb55b0747a327ade
ms.lasthandoff: 02/24/2017

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
 指定目标的表示方式。 表示可以包括内容、 图标、 一个缩略图或打印的文档。 有关可能的值的列表，请参阅[DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)和[DVASPECT2](http://msdn.microsoft.com/library/windows/desktop/ms688644)。  
  
 **索引**  
 与绘制操作有关的值得关注的目标的部分。 中的值而异解释**dwDrawAspect**成员。  
  
 **ptd**  
 指向[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)启用绘制优化根据所指定的方面的结构。 请注意，较新的对象和容器支持优化绘图接口的支持以及此成员。 较旧的对象和容器，始终不支持优化绘图接口指定**NULL**为此成员。  
  
 **hicTargetDev**  
 指向目标设备的信息上下文**ptd**对象可以从其提取设备量度并测试设备的功能。 如果**ptd**是**NULL**，该对象应忽略中的值**hicTargetDev**成员。  
  
 **hdcDraw**  
 在其上绘制的设备上下文。 对于无窗口对象， **hdcDraw**成员处于`MM_TEXT`以匹配包含窗口的工作区坐标其逻辑坐标表示的映射模式。 此外，设备上下文应该是相同的状态为正常情况下通过传递`WM_PAINT`消息。  
  
 **prcBounds**  
 指向[RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907)结构，它在指定矩形**hdcDraw**和在绘制该对象。 此成员控制的定位和拉伸的对象。 此成员应**NULL**绘制无窗口处于就地活动对象。 在每个其他情况下， **NULL**的合法值并不应导致`E_INVALIDARG`错误代码。 如果该容器通过非**NULL**无窗口对象，该对象的值应为指定的设备上下文和矩形呈现请求的方面。 一个容器可以请求从要呈现该对象的第二个、 非活动视图，或打印对象的无窗口对象。  
  
 **prcWBounds**  
 如果**hdcDraw**是图元文件设备上下文 (请参阅[GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)])，这是一个指向**RECTL**结构在基础元文件中指定的绑定矩形。 该矩形结构包含窗口 extent 和窗口原点。 这些值可用于绘制图元文件。 指示该矩形**prcBounds**嵌套在此**prcWBounds**矩形; 它们处于相同的坐标空间。  
  
 **bOptimize**  
 如果该控件的绘图是经过优化，否则为 0，非零值。 在完成时，如果经过了优化绘图，会自动还原设备上下文的状态呈现。  
  
 **bZoomed**  
 如果目标具有比例系数，否则为 0，非零值。 缩放系数存储在**ZoomNum**。  
  
 **bRectInHimetric**  
 如果非零的尺寸**prcBounds**位于**HIMETRIC**，否则为 0。  
  
 **ZoomNum**  
 宽度和呈现该对象的矩形的高度。 沿 x 轴 （其当前范围内的对象的原始大小的比例） 目标的缩放系数的价值是**ZoomNum.cx**的值除以**ZoomDen.cx**。 沿 y 轴缩放系数是以类似的方式实现的。  
  
 **ZoomDen**  
 实际宽度和高度的目标。  
  
## <a name="remarks"></a>备注  
 此结构的典型用法是信息的检索在目标对象呈现过程。 例如，可以检索来自值`ATL_DRAWINFO`内您重载[CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)。  
  
 此结构可存储用于呈现的目标设备对象外观的相关信息。 提供的信息可在绘制到屏幕、 打印机或甚至图元文件。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
## <a name="see-also"></a>另请参阅  
 [结构](../../atl/reference/atl-structures.md)   
 [Iviewobject:: Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)   
 [CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)






