---
title: 弃用 （C/c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
dev_langs:
- C++
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2280d5245292625bfc29815475eaca63d4d500bd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839814"
---
# <a name="deprecated-cc"></a>已弃用 (C/C++)
**弃用**杂注，可以指示，函数、 类型或任何其他标识符可能不再支持在将来版本支持或者应不再使用。  
> [!NOTE]
> 有关 C + + 14`[[deprecated]]`属性，以及有关何时使用该指导属性 vs Microsoft declspec 或杂注，请参阅[c + + 标准特性](../cpp/attributes.md)属性。
  
## <a name="syntax"></a>语法  
  
```  
#pragma deprecated( identifier1 [,identifier2, ...] )  
```  
  
## <a name="remarks"></a>备注  
 当编译器遇到指定的标识符**弃用**杂注，它会发出编译器警告[C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)。   
  
 可以否决宏名称。 将宏名称包含在引号内，否则宏将展开。  
  
 因为**弃用**杂注适用于所有匹配的标识符，并不会考虑签名，它不是要弃用的特定版本的重载函数的最佳选项。 置于范围的任何匹配的函数名称将触发警告。

  我们建议你使用 C + + 14`[[deprecated]]`属性，如果可能，而不是**弃用**杂注。 特定于 Microsoft 的[__declspec （deprecated)](../cpp/deprecated-cpp.md)声明修饰符也是更好的选择，在许多情况下比**弃用**杂注。 `[[deprecated]]`属性和`__declspec(deprecated)`修饰符允许你指定的特定形式的重载函数的不推荐使用的状态。 诊断警告仅出现在对特定的重载函数的引用属性还是适用于的修饰符。  
  
## <a name="example"></a>示例  
  
```  
// pragma_directive_deprecated.cpp  
// compile with: /W3  
#include <stdio.h>  
void func1(void) {  
}  
  
void func2(void) {  
}  
  
int main() {  
   func1();  
   func2();  
   #pragma deprecated(func1, func2)  
   func1();   // C4995  
   func2();   // C4995  
}  
```  
  
 以下示例说明如何否决类：  
  
```  
// pragma_directive_deprecated2.cpp  
// compile with: /W3  
#pragma deprecated(X)  
class X {  // C4995  
public:  
   void f(){}  
};  
  
int main() {  
   X x;   // C4995  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)