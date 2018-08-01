---
title: ABI 边界 （现代 C++） 处的可移植性 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb9ce8012db8617afc7af3183bd7439ddeb8fab7
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402346"
---
# <a name="portability-at-abi-boundaries-modern-c"></a>ABI 边界处的可移植性（现代 C++）
在二进制接口边界使用二进制接口边界类型和约定。 “可迁移类型”是 C 内置类型或包含 C 内置类型的结构。 当调用方和被调用方接受布局、 调用约定等时，可以仅使用类类型。这种情况只有时都使用相同的编译器和编译器设置编译。  
  
## <a name="how-to-flatten-a-class-for-c-portability"></a>如何为了 C 可移植性平展类  
 当调用方可能会使用另一编译器/语言编译，则"平展"为**extern"C"** 使用特定的调用约定的 API:  
  
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