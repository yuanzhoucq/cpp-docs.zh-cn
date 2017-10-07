---
title: "已过时调用约定 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __fortran
- __pascal
- __syscall
dev_langs:
- C++
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 90f328552677bc0f41accc316433365467dd7673
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="obsolete-calling-conventions"></a>已过时调用约定
## <a name="microsoft-specific"></a>Microsoft 专用  
 **__Pascal**， **__fortran**，和**__syscall**调用约定不再受支持。 通过使用支持的调用约定之一和适当的链接器选项，可以模拟其功能。  
  
 WINDOWS。H 现在支持**WINAPI**宏，将转换为目标的适当调用约定。 使用**WINAPI**以前使用**PASCAL**或**__far \__pascal**。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [自变量传递和命名约定](../cpp/argument-passing-and-naming-conventions.md)
