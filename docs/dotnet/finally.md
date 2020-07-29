---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: b3331c17fc2313cbd6146db3beb015cd8d8c1eeb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221453"
---
# <a name="finally"></a>finally

除 **`try`** 和子句外 **`catch`** ，CLR 异常处理还支持 **`finally`** 子句。 语义与 **`__finally`** 结构化异常处理（SEH）中的块完全相同。 **`__finally`** 块可以跟在 **`try`** 或块之后 **`catch`** 。

## <a name="remarks"></a>备注

此块的用途 **`finally`** 是在发生异常后清理剩余的资源。 请注意， **`finally`** 即使未引发异常，也始终会执行块。 **`catch`** 仅当关联的块中引发了托管异常时，才会执行块 **`try`** 。

`finally`是上下文相关的关键字;有关详细信息，请参阅[上下文相关的关键字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例演示一个简单的 **`finally`** 块：

```cpp
// keyword__finally.cpp
// compile with: /clr
using namespace System;

ref class MyException: public System::Exception{};

void ThrowMyException() {
   throw gcnew MyException;
}

int main() {
   try {
      ThrowMyException();
   }
   catch ( MyException^ e ) {
      Console::WriteLine(  "in catch" );
      Console::WriteLine( e->GetType() );
   }
   finally {
      Console::WriteLine(  "in finally" );
   }
}
```

```Output
in catch
MyException
in finally
```

## <a name="see-also"></a>另请参阅

[异常处理](../extensions/exception-handling-cpp-component-extensions.md)
