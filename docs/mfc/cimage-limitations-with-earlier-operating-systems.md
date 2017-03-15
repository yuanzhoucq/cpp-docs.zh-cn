---
title: "早期操作系统中的 CImage 限制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CImage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CImage 类, 限制"
ms.assetid: 4bedaab8-7dd1-4c91-ab35-b75fb56765b0
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 早期操作系统中的 CImage 限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

许多 `CImage` 函数仅适用于 Windows 新版本：Windows 95\/98 或 Windows NT 4.0、Windows 2000。  本文介绍某些方法的版本限制。  
  
 [CImage::PlgBlt](../Topic/CImage::PlgBlt.md) 和 [CImage::MaskBlt](../Topic/CImage::MaskBlt.md) 只与 Windows NT 4.0 或更高版本一起使用。  它们在运行 Windows 95\/98 或更高版本的应用程序上不起作用。  
  
 [CImage::AlphaBlend](../Topic/CImage::AlphaBlend.md) 和 [CImage::TransparentBlt](../Topic/CImage::TransparentBlt.md) 仅适用于 Windows 2000 或之后版本和 Windows 98 或之后版本，因为您必须使用这些方法链接 msimg32.lib。\(该库仅适用于运行 Windows 2000 或之后版本和 Windows 98 或之后版本的应用程序。\)  
  
 可以包含 `AlphaBlend` 和 `TransparentBlt` 在 Windows 95 或 Windows NT 4.0 上运行的应用程序时，如果，没有调用这些方法。  如果应用程序包括了这些方法，并且必须运行在以前的操作系统，您必须使用链接器的 [\/delayload](../build/reference/delayload-delay-load-import.md) 来延迟加载 msimg32.lib。  只要应用程序运行在 Windows NT 4.0 或 Windows 95 上时不调用其中任一方法，它不会尝试加载 msimg32.lib。  您可以可使用 `CImage::IsTransparencySupported` 方法检查是否支持透明度。  
  
## 示例  
 [!code-cpp[NVC_MFCDocViewSDI#8](../mfc/codesnippet/CPP/cimage-limitations-with-earlier-operating-systems_1.cpp)]  
  
 若要编译调用这些方法的应用程序，请在 \#including 任何系统头文件前插入 \#define \_WIN32\_WINNT 语句，指出 Windows 版本大于或等于 5.0:  
  
 [!code-cpp[NVC_MFCDocViewSDI#9](../mfc/codesnippet/CPP/cimage-limitations-with-earlier-operating-systems_2.h)]  
  
 如果应用程序不需要运行在比 Windows 2000 或 Windows 98 更老的系统上，则可不使用 **\/delayload** 直接链接到 msimg32.lib。  
  
 [CImage::Draw](../Topic/CImage::Draw.md) 在用于 Windows 2000 和 Windows 98 和用于 Windows NT 4.0 或 Windows 95 时行为不同。  
  
 如果伴随值小于 0x0500 的 \_WIN32\_WINNT 编译应用程序， **Draw** 将会起作用，但是，它在运行 Windows 2000 和 Windows 98 上或之后的系统上时不会自动处理透明度。  
  
 如果伴随值大于 0x0500 的 \_WIN32\_WINNT 编译应用程序设， **Draw** 在运行 Windows 2000 或 Windows 98 或之后的系统上时将自动处理透明度。  在 Windows NT 4.0 和 Windows 95上它还将起作用，但无需透明度支持;但是，必须使用 **\/delayload** 延迟加载 msimg32.LIB，如上为 `AlphaBlend` 和 `TransparentBlt` 所述。  
  
## 请参阅  
 [CImage Class](../atl-mfc-shared/reference/cimage-class.md)