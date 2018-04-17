---
title: "ABI 边界 （现代 C++） 处的可移植性 |Microsoft 文档"
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
caps.latest.revision: 4
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 06cb6c97580b4c4c9a6c961cb76f2c4d84d841ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="portability-at-abi-boundaries-modern-c"></a>ABI 边界处的可移植性（现代 C++）
在二进制接口边界使用二进制接口边界类型和约定。 “可迁移类型”是 C 内置类型或包含 C 内置类型的结构。 当调用方和被调用方同意布局，调用约定，等等，则仅可以使用类类型。这种情况只有，同时使用同一编译器和编译器设置在编译时。  
  
## <a name="how-to-flatten-a-class-for-c-portability"></a>如何为了 C 可移植性平展类  
 如果调用方可能使用另一编译器/语言编译，则"平展"为**extern"C"**使用特定调用约定的 API:  
  
```cpp  
// class widget {  
//   widget();  
//   ~widget();  
//   double method( int, gadget& );  
// };  
extern "C" {        // functions using explicit "this"  
   struct widget;   // opaque type (forward declaration only)  
   widget* STDCALL widget_create();      // constructor creates new "this"  
   void STDCALL widget_destroy(widget*); // destructor consumes "this"  
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [欢迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C++ 语言参考](../cpp/cpp-language-reference.md)   
 [C++ 标准库](../standard-library/cpp-standard-library-reference.md)