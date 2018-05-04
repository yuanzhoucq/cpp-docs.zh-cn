---
title: __uuidof 运算符 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
dev_langs:
- C++
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 70731665ca2a2eba739f139678e0f7eaface2b85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="uuidof-operator"></a>__uuidof 运算符
**Microsoft 专用**  
  
 检索附加到表达式的 GUID。  
  
## <a name="syntax"></a>语法  
  
```  
  
      __uuidof (  
   expression   
)  
```  
  
## <a name="remarks"></a>备注  
 *表达式*可以是类型名称、 指针、 引用或该类型的数组，模板专用化对这些类型或这些类型的变量。 只要编译器可使用自变量查找附加的 GUID，此自变量就有效。  
  
 此内部函数的一个特殊情况是当任一**0**或**NULL**作为参数提供。 在此情况下，`__uuidof` 将返回由零组成的 GUID。  
  
 使用此关键字可将附加的 GUID 提取到：  
  
-   一个对象的[uuid](../cpp/uuid-cpp.md)扩展的特性。  
  
-   使用创建的库块[模块](../windows/module-cpp.md)属性。  
  
> [!NOTE]
>  在调试版本中，`__uuidof` 始终动态初始化对象（在运行时）。 在发布版本中，`__uuidof` 可静态初始化对象（在编译时）。  
  
## <a name="example"></a>示例  
 以下代码（使用 ole32.lib 编译的）将显示使用 module 特性创建的库块的 uuid。  
  
```  
// expre_uuidof.cpp  
// compile with: ole32.lib  
#include "stdio.h"  
#include "windows.h"  
  
[emitidl];  
[module(name="MyLib")];  
[export]  
struct stuff {  
   int i;  
};  
  
int main() {  
   LPOLESTR lpolestr;  
   StringFromCLSID(__uuidof(MyLib), &lpolestr);  
   wprintf_s(L"%s", lpolestr);  
   CoTaskMemFree(lpolestr);  
}  
```  
  
## <a name="comments"></a>注释  
 在中库名不再在作用域中的情况下，你可以使用 __LIBID\_而不是`__uuidof`。 例如：  
  
```  
StringFromCLSID(__LIBID_, &lpolestr);  
```  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [关键字](../cpp/keywords-cpp.md)