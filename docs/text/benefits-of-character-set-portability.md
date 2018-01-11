---
title: "字符的好处设置可移植性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 554137352c0a8f7275a051e4026020fce25edbb8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="benefits-of-character-set-portability"></a>字符集可迁移性的好处
你可以从使用 MFC 和 C 运行时可移植性功能，即使你不当前打算国际化应用程序受益：  
  
-   移植编码使代码基更灵活。 你可以稍后将其移轻松地为 Unicode 或 MBCS。  
  
-   使用 Unicode 使 Windows 2000 的应用程序更高效。 由于 Windows 2000 使用 Unicode，必须转换传递到和从操作系统的非 Unicode 字符串，这可能会产生开销。  
  
-   使用 MBCS，可在 Windows 2000，如 Windows 95 或 Windows 98 以外的 Win32 平台上支持国际市场。  
  
## <a name="see-also"></a>请参阅  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [支持 Unicode](../text/support-for-unicode.md)