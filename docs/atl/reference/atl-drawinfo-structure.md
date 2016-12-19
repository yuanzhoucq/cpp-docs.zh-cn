---
title: "ATL_DRAWINFO Structure | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::ATL_DRAWINFO"
  - "ATL_DRAWINFO"
  - "ATL.ATL_DRAWINFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL_DRAWINFO structure"
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL_DRAWINFO Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含用于呈现用于的信息多个目标，如打印机、图元文件或ActiveX控件。  
  
## 语法  
  
```  
  
      struct ATL_DRAWINFO{  
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
  
## 成员  
 `cbSize`  
 结构的大小，以字节为单位）。  
  
 **dwDrawAspect**  
 指定目标如何将表示。  表示可以包括目录，图标，缩略图，或者打印的文档。  有关可能值列表，请参见 [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) 和 [DVASPECT2](http://msdn.microsoft.com/library/windows/desktop/ms688644)。  
  
 **lindex**  
 是绘制操作的利益目标的部分。  其解释基于 **dwDrawAspect** 成员的值而异。  
  
 **ptd**  
 根据指定的这种方式启用绘制优化的 [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) 结构的指针。  请注意支持优化绘制的接口的较新的对象和容器支持此成员。  不支持优化绘制的接口的较旧的对象和容器对该成员始终指定 **NULL**。  
  
 **hicTargetDev**  
 目标设备的信息上下文指向由对象可以提取设备指标的 **ptd** 和测试工具的功能。  如果 **ptd** 是 **NULL**，对象应忽略在 **hicTargetDev** 成员的值。  
  
 **hdcDraw**  
 的设备上下文绘制的。  对于无窗口的对象，这些对象是在 `MM_TEXT` 映射到其逻辑坐标的 **hdcDraw** 成员模式匹配包含窗口的工作区坐标。  此外，设备上下文应处于状态和 `WM_PAINT` 消息通常通过所在的同一。  
  
 **prcBounds**  
 为 [RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907) 结构的指针指定矩形中 **hdcDraw** 和在哪个绘制对象。  此成员控件定位和拉伸对象。  该成员应是绘制一个无窗口的就地活动对象的 **NULL**。  在其他情况下，**NULL** 不是一个合法的值，并且应生成 `E_INVALIDARG` 错误代码。  如果容器通过非**NULL** 值传递给无窗口的对象，应呈现请求的方面到指定的设备上下文和矩形。  容器可以请求此从一个无窗口的对象呈现对象的第二个，非活动视图或输出对象。  
  
 **prcWBounds**  
 如果 **hdcDraw** 是图元文件设备上下文\(参见中 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877) \)，这是对 **RECTL** 结构指定边框的某个基础图元文件。  矩形结构包含windows区域和windows原点。  这些值将绘制图元文件非常有用。  **prcBounds** 表示的矩形嵌套在此 **prcWBounds** 矩形内部;在相同的坐标空间。  
  
 **bOptimize**  
 非零，如果控件的绘图进行优化，否则0。  如果绘制了优化，自动还原设备上下文的状态，当您完成呈现时。  
  
 **bZoomed**  
 非零，如果目标有一个比例因子，否则0。  比例因子在 **ZoomNum**存储。  
  
 **bRectInHimetric**  
 非零，则维度 **prcBounds** 在 **HIMETRIC**;否则为0。  
  
 **ZoomNum**  
 对象呈现矩形的宽度和高度。  沿X轴\(对象的原始大小的比例的缩放比例在其当前程度\)在目标为 **ZoomNum.cx** 的值。**ZoomDen.cx**的值部件。  沿y轴的缩放比例来实现。  
  
 **ZoomDen**  
 目标的实际宽度和高度。  
  
## 备注  
 在呈现目标对象时，此结构典型用法是检索信息。  例如，可以在 [CComControlBase::OnDrawAdvanced](../Topic/CComControlBase::OnDrawAdvanced.md)内对重载的 `ATL_DRAWINFO` 检索值。  
  
 此结构存储用于的相关信息呈现对象的外观目标设备的。  所提供的信息可用于对屏幕、打印机，甚至图元文件的绘图。  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [结构](../../atl/reference/atl-structures.md)   
 [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)   
 [CComControlBase::OnDrawAdvanced](../Topic/CComControlBase::OnDrawAdvanced.md)