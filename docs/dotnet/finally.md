---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: 2574ba5a10bbf5eddc68d6e0265d5dfc99c6d8fc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545095"
---
# <a name="finally"></a>finally

除了 `try` 和 `catch` 子句外，CLR 异常处理还支持 `finally` 子句。 语义与结构化异常处理（SEH）中的 `__finally` 块相同。 `__finally` 块可以遵循 `try` 或 `catch` 块。

## <a name="remarks"></a>备注

`finally` 块的用途是在发生异常后清理剩余的资源。 请注意，即使未引发异常，也始终会执行 `finally` 块。 仅当关联的 `try` 块内引发了托管异常时，才会执行 `catch` 块。

`finally` 是区分上下文的关键字;有关详细信息，请参阅[上下文相关的关键字](../extensions/context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例演示一个简单的 `finally` 块：

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
