---
title: 如何：在本机代码中捕捉从 MSIL 引发的异常
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: 6f2de640a2427bb1ea65d099742967454ca625f6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221349"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>如何：在本机代码中捕捉从 MSIL 引发的异常

在本机代码中，可以从 MSIL 捕获本机 c + + 异常。  您可以用和捕获 CLR `__try` 异常 **`__except`** 。

有关详细信息，请参阅[结构化异常处理（C/c + +）](../cpp/structured-exception-handling-c-cpp.md)和[异常和错误处理的新式 c + + 最佳实践](../cpp/errors-and-exception-handling-modern-cpp.md)。

## <a name="example"></a>示例

下面的示例定义一个包含两个函数的模块，其中一个函数引发本机异常，另一个引发 MSIL 异常。

```cpp
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

下面的示例定义了一个模块，该模块捕获本机和 MSIL 异常。

```cpp
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

## <a name="see-also"></a>另请参阅

[异常处理](../extensions/exception-handling-cpp-component-extensions.md)
