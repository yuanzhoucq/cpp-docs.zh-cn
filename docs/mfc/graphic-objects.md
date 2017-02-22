---
title: "图形对象 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "HRGN"
  - "HFONT"
  - "HBITMAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - " [C++], 在设备上下文中创建"
  - "画笔, 在设备上下文中创建"
  - "CBitmap 类, HBITMAP 句柄类型"
  - "CBrush 类, HBRUSH 句柄类型"
  - "CFont 类, HFONT 句柄类型"
  - "CPalette 类, HPALETTE 句柄类型"
  - "CPen 类, HPEN 句柄类型"
  - "CRgn 类, HRGN 句柄类型"
  - "设备上下文, 图形对象"
  - "绘图, 在设备上下文中"
  - "字体 [C++], 在设备上下文中创建"
  - "GDI [C++], 图形对象类"
  - "GDI 对象 [C++]"
  - "GDI 对象 [C++], 图形对象类"
  - "图形对象"
  - "图形对象, 在设备上下文中创建"
  - "HBITMAP 和类 CBitmap"
  - "HBRUSH 和类 CBrush"
  - "HFONT 和类 CFont"
  - "HPALETTE 和类 CPalette"
  - "HPEN"
  - "HRGN"
  - "图像 [C++], 图形对象"
  - "内存 [C++], 显示上下文"
  - "MFC, 图形对象"
  - "对象 [C++], 图形"
  - "对象 [C++], 图形对象"
  - "绘制和设备上下文"
  - "调色板对象"
  - "调色板, 在设备上下文中创建"
  - "钢笔对象"
  - "钢笔, 在设备上下文中创建"
  - "区域对象"
  - "区域, 在设备上下文中创建"
ms.assetid: 41963b25-34b7-4343-8446-34ba516b83ca
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 图形对象
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Windows 提供了各种可在设备上下文中使用的绘图工具。  它提供了用于绘制线条的笔、用于填充内部的画笔以及用于绘制文本的字体。  MFC 提供等效于 Windows 中的绘图工具的图形对象类。  下表显示可用类以及等效的 Windows 图形设备接口 \(GDI\) 句柄类型。  
  
> [!NOTE]
>  GDI\+ 随 Windows XP 附带，可用作 Windows NT 4.0 SP6、Windows 2000、Windows 98 和 Windows Me 的可再发行组件。  若要下载最新可再发行组件，请参阅 [http:\/\/www.microsoft.com\/msdownload\/platformsdk\/sdkupdate\/psdkredist.htm](http://www.microsoft.com/msdownload/platformsdk/sdkupdate/psdkredist.htm)。  有关详细信息，请参阅 MSDN 中的 GDI\+ SDK 文档：[http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/gdicpp\/GDIPlus\/GDIPlus.asp](http://msdn.microsoft.com/library/default.asp?url=/library/gdicpp/GDIPlus/GDIPlus.asp)。  
  
 本文说明了这些图形对象类的用法：  
  
### 用于 Windows GDI 对象的类  
  
|类|Windows 句柄类型|  
|-------|------------------|  
|[CPen](../mfc/reference/cpen-class.md)|`HPEN`|  
|[CBrush](../mfc/reference/cbrush-class.md)|`HBRUSH`|  
|[CFont](../mfc/reference/cfont-class.md)|**HFONT**|  
|[CBitmap](../mfc/reference/cbitmap-class.md)|`HBITMAP`|  
|[CPalette](../mfc/reference/cpalette-class.md)|`HPALETTE`|  
|[CRgn](../mfc/reference/crgn-class.md)|**HRGN**|  
  
> [!NOTE]
>  类 [CImage](../atl-mfc-shared/reference/cimage-class.md) 提供增强的位图支持。  
  
 类库中的每个图形对象类都具有一个构造函数，使你可以创建该类的图形对象，随后必须使用适当的创建函数（如 `CreatePen`）初始化这些对象。  
  
 类库中的每个图形对象类都具有一个强制转换运算符，可将 MFC 对象强制转换为关联的 Windows 句柄。  生成的句柄在关联对象将它分离之前都有效。  使用对象的 **Detach** 成员函数可分离句柄。  
  
 下面的代码将 `CPen` 对象强制转换为 Windows 句柄：  
  
 [!code-cpp[NVC_MFCDocViewSDI#5](../mfc/codesnippet/CPP/graphic-objects_1.cpp)]  
  
#### 在设备上下文中创建图形对象  
  
1.  在堆栈帧上定义图形对象。  使用特定于类型的创建函数（如 `CreatePen`）初始化对象。  或者，在构造函数中初始化对象。  请参阅[一阶段和两阶段构造](../mfc/one-stage-and-two-stage-construction-of-objects.md)的讨论，其中提供了示例代码。  
  
2.  [选择对象进入当前设备上下文中](../mfc/selecting-a-graphic-object-into-a-device-context.md)，从而保存以前选择的旧图形对象。  
  
3.  处理了当前图形对象之后，选择旧图形对象返回设备上下文以还原其状态。  
  
4.  允许在退出范围时自动删除帧分配的图形对象。  
  
> [!NOTE]
>  如果重复使用图形对象，则可以分配它一次，然后在每次需要时选择它进入设备上下文中。  请务必在不再需要时删除这类对象。  
  
### 你想进一步了解什么？  
  
-   [图形对象的一阶段和两阶段构造](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [采用一或两个阶段构造笔的示例](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [将图形对象选入设备上下文](../mfc/selecting-a-graphic-object-into-a-device-context.md)  
  
-   [设备上下文](../mfc/device-contexts.md)  
  
-   [早期操作系统中的 CImage 限制](../mfc/cimage-limitations-with-earlier-operating-systems.md)  
  
## 请参阅  
 [窗口对象](../mfc/window-objects.md)