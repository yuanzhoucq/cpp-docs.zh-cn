---
title: 字符的好处设置可移植性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d1b78048baebfd89aed0ccc898c2bb9e3612525
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="benefits-of-character-set-portability"></a>字符集可迁移性的好处
你可以从使用 MFC 和 C 运行时可移植性功能，即使你不当前打算国际化应用程序受益：  
  
-   移植编码使代码基更灵活。 你可以稍后将其移轻松地为 Unicode 或 MBCS。  
  
-   使用 Unicode 使适用于 Windows 应用程序更高效。 由于 Windows 使用 Unicode，必须转换传递到和从操作系统的非 Unicode 字符串，这可能会产生开销。  

  
## <a name="see-also"></a>请参阅  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [支持 Unicode](../text/support-for-unicode.md)