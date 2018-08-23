---
title: 如何： 在从 MSIL 引发的本机代码中捕捉异常 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3d5c1efde1f98ac3f9fdccb19039373d5cfe6be6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127872"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>如何：在本机代码中捕捉从 MSIL 引发的异常
在本机代码中，你可以捕获自 MSIL 的本机 c + + 异常。  你可以捕获 CLR 异常`__try`和`__except`。  
  
 有关详细信息，请参阅[结构化异常处理 （C/c + +）](../cpp/structured-exception-handling-c-cpp.md)和[c + + 异常处理](../cpp/cpp-exception-handling.md)。  
  
## <a name="example"></a>示例  
 下面的示例定义的模块的两个函数、 一个引发本机异常，而另一个引发 MSIL 异常。  
  
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