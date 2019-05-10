---
title: 如何：在从 MSIL 引发的本机代码中捕捉异常
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: 95ce7a2afabc34ea78376b12da61f419dab4af34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62379034"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>如何：在从 MSIL 引发的本机代码中捕捉异常

在本机代码中，可以捕获本机C++从 MSIL 的异常。  您可以捕获与 CLR 异常`__try`和`__except`。

有关详细信息，请参阅[结构化异常处理 (C /C++)](../cpp/structured-exception-handling-c-cpp.md)并[C++的异常处理](../cpp/cpp-exception-handling.md)。

## <a name="example"></a>示例

下面的示例定义引发 MSIL 异常与两个函数，将引发本机异常，其中一个，另一个模块。

```
// catch_MSIL_in_native.cpp
// compile with: /clr /c
void Test() {
   throw ("error");
}

void Test2() {
   throw (gcnew System::Exception("error2"));
}
```

## <a name="example"></a>示例

下面的示例定义一个模块，将捕获本机和 MSIL 的异常。

```
// catch_MSIL_in_native_2.cpp
// compile with: /clr catch_MSIL_in_native.obj
#include <iostream>
using namespace std;
void Test();
void Test2();

void Func() {
   // catch any exception from MSIL
   // should not catch Visual C++ exceptions like this
   // runtime may not destroy the object thrown
   __try {
      Test2();
   }
   __except(1) {
      cout << "caught an exception" << endl;
   }

}

int main() {
   // catch native C++ exception from MSIL
   try {
      Test();
   }
   catch(char * S) {
      cout << S << endl;
   }
   Func();
}
```

```Output
error
caught an exception
```

## <a name="see-also"></a>请参阅

[异常处理](../extensions/exception-handling-cpp-component-extensions.md)
