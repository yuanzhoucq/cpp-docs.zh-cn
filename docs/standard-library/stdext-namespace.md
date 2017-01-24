---
title: "stdext 命名空间 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_DEFINE_DEPRECATED_HASH_CLASSES 符号"
  - "stdext 命名空间"
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# stdext 命名空间
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

标头文件的成员 [\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](../standard-library/hash-set.md) 当前不是 ISO C\+\+ 标准的一部分。 因此，这些类型和成员已从 `std` 命名空间移动到命名空间 `stdext` 以保持符合 C\+\+ 标准。  
  
 当使用默认的 [\/Ze](../build/reference/za-ze-disable-language-extensions.md) 进行编译时，该编译器将针对 \<hash\_map\> 标头文件和 \<hash\_set\> 标头文件的成员警告 `std` 的使用。 若要禁用该警告，请使用[警告](../preprocessor/warning.md)杂注。  
  
 若要让编译器在 \<hash\_map\> 标头文件和 \<hash\_set\> 标头文件的成员将 `std` 用于 **\/Ze** 时生成错误，则在包括任何标准 C\+\+ 库标头文件之前添加以下指令。  
  
```  
#define _DEFINE_DEPRECATED_HASH_CLASSES 0  
```  
  
 使用 **\/Za** 进行编译时，该编译器将生成一个错误。  
  
## 请参阅  
 [STL 概述](../standard-library/cpp-standard-library-overview.md)