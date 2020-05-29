---
title: 如何：在本机代码中捕捉从 MSIL 引发的异常
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: 23adb573a62e93933c487f611c05aed4c08494ef
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545083"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>如何：在本机代码中捕捉从 MSIL 引发的异常

在本机代码中，可以从 MSIL C++捕获本机异常。  您可以 `__try` 和 `__except`中捕获 CLR 异常。

有关详细信息，请参阅[结构化异常处理（C++C/）](../cpp/structured-exception-handling-c-cpp.md)和[异常和错误处理的新式C++最佳实践](../cpp/errors-and-exception-handling-modern-cpp.md)。

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
