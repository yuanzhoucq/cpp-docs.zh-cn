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
caps.latest.revision: 14
author: corob-msft
ms.author: corob
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 0eb057f9d229c659f339f996d1ff38f65fd2e018
ms.openlocfilehash: be461857f4aa1625094b20a2241ab15853d2aa81
ms.contentlocale: zh-cn
ms.lasthandoff: 06/01/2017

---
# <a name="windows-runtime-unsupported-crt-functions"></a>Windows 运行时不支持的 CRT 函数
许多 C 运行时 (CRT) API 都不能用于在 Windows 运行时中执行的 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用。 这些应用是使用 /ZW 编译器标志生成的。 有关不支持的 CRT 函数的列表，请参阅[/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
 文档的[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)部分介绍了所有 CRT API。  
  
## <a name="see-also"></a>另请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
