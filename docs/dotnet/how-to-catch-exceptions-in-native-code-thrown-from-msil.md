---
title: 如何：在本机代码中捕捉从 MSIL 引发的异常
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: 73c9a9af66a6e292c76b96ec47a5853684e602f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635579"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>如何：在本机代码中捕捉从 MSIL 引发的异常

在本机代码中，可以捕捉从 MSIL 的本机 c + + 异常。  您可以捕获与 CLR 异常`__try`和`__except`。

有关详细信息，请参阅[结构化异常处理 （C/c + +）](../cpp/structured-exception-handling-c-cpp.md)并[c + + 异常处理](../cpp/cpp-exception-handling.md)。

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

[异常处理](../windows/exception-handling-cpp-component-extensions.md)