---
title: "早期操作系统中的 CImage 限制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CImage
dev_langs:
- C++
helpviewer_keywords:
- CImage class [MFC], limitations
ms.assetid: 4bedaab8-7dd1-4c91-ab35-b75fb56765b0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27046704975bf8f5e28f12acbfa72e860660fdbd
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2018
---
# <a name="cimage-limitations-with-earlier-operating-systems"></a>早期操作系统中的 CImage 限制
很多 `CImage` 函数仅适用于较新的 Windows 版本：Windows 95/98、Windows NT 4.0 或 Windows 2000。 本文介绍某些方法的版本限制。  
  
 [Cimage:: Plgblt](../atl-mfc-shared/reference/cimage-class.md#plgblt)和[cimage:: Maskblt](../atl-mfc-shared/reference/cimage-class.md#maskblt)仅适用于 Windows NT 4.0 或更高版本。 它们对运行 Windows 95/98 或更高版本的应用程序不起作用。  
  
 [Cimage:: Alphablend](../atl-mfc-shared/reference/cimage-class.md#alphablend)和[cimage:: Transparentblt](../atl-mfc-shared/reference/cimage-class.md#transparentblt)仅适用于 Windows 2000 或更高版本以及 Windows 98 或更高，因为你必须与 msimg32.lib 链接才能使用这些方法。 （该库仅可用于运行 Windows 2000 或更高版本以及 Windows 98 或更高版本的应用程序。）  
  
 仅当从未调用过 `AlphaBlend` 和 `TransparentBlt` 时，您才能将这些方法包含在 Windows 95 或 Windows NT 4.0 上运行的应用程序中。 如果你的应用程序包含这些方法，并且它必须在早期版本的操作系统上运行，则必须使用链接器的[/delayload](../build/reference/delayload-delay-load-import.md)延迟加载 msimg32.lib。 只要应用程序在运行于 Windows NT 4.0 或 Windows 95 下时未调用这些方法之一，它就不会尝试加载 msimg32.lib。 您可以使用 `CImage::IsTransparencySupported` 方法检查透明度支持是否可用。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocViewSDI#8](../mfc/codesnippet/cpp/cimage-limitations-with-earlier-operating-systems_1.cpp)]  
  
 若要编译调用这些方法的应用程序，请在使用 #including 包含任何系统标头前插入 #define _WIN32_WINNT 语句，并指明 Windows 的版本等于或高于 5.0：  
  
 [!code-cpp[NVC_MFCDocViewSDI#9](../mfc/codesnippet/cpp/cimage-limitations-with-earlier-operating-systems_2.h)]  
  
 如果你的应用程序并不需要运行早于 Windows 2000 或 Windows 98 的操作系统上，你可以直接链接到 msimg32.lib 而无需使用**/delayload**。  
  
 [Cimage:: Draw](../atl-mfc-shared/reference/cimage-class.md#draw)以不同方式在用于 Windows 2000 和 Windows 98，与用于 Windows NT 4.0 或 Windows 95 时的行为。  
  
 如果编译你的应用程序时将 _WIN32_WINNT 设置为一个值小于 0x0500 的值，**绘制**工作，但它将不会处理自动在运行 Windows 2000 和 Windows 98 及更高版本的系统上的透明度。  
  
 如果你的应用程序时将 _WIN32_WINNT 设置为等于 0x0500 的值或更高版本进行编译**绘制**将处理自动在运行 Windows 2000 或 Windows 98 及更高版本的系统上的透明度。 它也适用，但不支持透明度错误，使用 Windows NT 4.0 和 Windows 95;但是，你必须使用**/delayload**延迟 msimg32 加载。LIB，如上文所述的`AlphaBlend`和`TransparentBlt`。  
  
## <a name="see-also"></a>请参阅  
 [CImage 类](../atl-mfc-shared/reference/cimage-class.md)
