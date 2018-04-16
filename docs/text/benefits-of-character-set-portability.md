---
title: "字符的好处设置可移植性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ce02fa834c39f629990d4f3c9785de94bd02196
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/09/2018
---
# <a name="benefits-of-character-set-portability"></a>字符集可迁移性的好处
你可以从使用 MFC 和 C 运行时可移植性功能，即使你不当前打算国际化应用程序受益：  
  
-   移植编码使代码基更灵活。 你可以稍后将其移轻松地为 Unicode 或 MBCS。  
  
-   使用 Unicode 使适用于 Windows 应用程序更高效。 由于 Windows 使用 Unicode，必须转换传递到和从操作系统的非 Unicode 字符串，这可能会产生开销。  

  
## <a name="see-also"></a>请参阅  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [支持 Unicode](../text/support-for-unicode.md)