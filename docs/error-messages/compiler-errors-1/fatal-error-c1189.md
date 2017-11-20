---
title: "错误 C1189 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1189
dev_langs: C++
helpviewer_keywords: C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e8d3c9ff44a436688accfe267141390d23c0eb5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1189"></a>错误 C1189
\#错误： 用户提供错误消息  
  
 由生成 C1189`#error`指令。 开发人员代码指令指定的错误消息的文本。 有关详细信息，请参阅[#error 指令 （C/c + +）](../../preprocessor/hash-error-directive-c-cpp.md)。  
  
 下面的示例生成 C1189。 在示例中，开发人员发出自定义错误消息，因为`_WIN32`未定义标识符：  
  
```  
// C1189.cpp  
#undef _WIN32  
#if !defined(_WIN32)  
#error _WIN32 must be defined   // C1189  
#endif  
```  
  
 你可能还会看到此错误，如果使用生成 ATL 项目**/ 可靠**MIDL 编译器选项。 使用**/ 可靠**开关可仅生成[!INCLUDE[win2kfamily](../../c-runtime-library/includes/win2kfamily_md.md)]和更高版本的 Windows。 请执行以下步骤以更正此错误：  
  
-   将此行 dlldatax.c 文件中的更改：  
  
```  
#define _WIN32_WINNT 0x0400   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
 更改为：  
  
```  
#define _WIN32_WINNT 0x0500   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
-   使用**高级**中的属性页**MIDL**要删除的属性页文件夹**/ 可靠**开关，然后指定**/no_robust**切换。 有关详细信息，请参阅[MIDL 属性页： 高级](../../ide/midl-property-pages-advanced.md)。  
  
## <a name="see-also"></a>另请参阅  
 [#define 指令 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)