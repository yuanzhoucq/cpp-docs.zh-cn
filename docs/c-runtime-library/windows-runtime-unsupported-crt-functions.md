---
title: "Windows 运行时不支持的 CRT 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- unsupported CRT functions, Windows Runtime
- Windows Runtime, unsupported CRT functions
ms.assetid: bb8386d6-0ef8-460c-88d8-addff009b6f1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a2f6b06b45da502e3eba898f2907042afeca65c2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="windows-runtime-unsupported-crt-functions"></a>Windows 运行时不支持的 CRT 函数
许多 C 运行时 (CRT) API 都不能用于在 Windows 运行时中执行的通用 Windows 平台应用。 这些应用是使用 /ZW 编译器标志生成的。 有关不支持的 CRT 函数的列表，请参阅[/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
 文档的[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)部分介绍了所有 CRT API。  
  
## <a name="see-also"></a>请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)