---
title: "编译器警告 （等级 4） C4481 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4481
dev_langs: C++
helpviewer_keywords: C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52c296251e22adef2702aa9feba2b1fe2bc5122e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4481"></a>编译器警告（等级 4）C4481
使用的非标准扩展： 重写说明符 keyword  
  
 使用不在 c + + 标准，例如，一个在 /clr 下也适用于重写说明符的关键字。  有关详细信息，请参阅  
  
-   [/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [重写说明符](../../windows/override-specifiers-cpp-component-extensions.md)  
  
## <a name="example"></a>示例  
 下面的示例生成 C4481。  
  
```  
// C4481.cpp  
// compile with: /W4 /c  
class B {  
   virtual void f(unsigned);  
};  
  
class C : B {  
   void f(unsigned) override;   // C4481  
   void f2(unsigned);  
};  
```