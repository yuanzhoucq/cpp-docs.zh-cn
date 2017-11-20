---
title: "编译器错误 C3551 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3551
dev_langs: C++
helpviewer_keywords: C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 450bd97efc9cfbf07eac84a3e6a693af698fc64f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3551"></a>编译器错误 C3551
“应为后期指定的返回类型”  
  
 如果你使用 `auto` 关键字作为函数返回类型的占位符，必须提供后指定返回类型。 在下面的示例中，函数 `myFunction` 的后期指定返回类型是一个指针，该指针指向由四个 `int`类型的元素组成的数组。  
  
```  
auto myFunction()->int(*)[4];   
```  
  
## <a name="see-also"></a>另请参阅  
 [auto](../../cpp/auto-cpp.md)