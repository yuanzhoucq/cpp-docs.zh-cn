---
title: finally
ms.date: 11/04/2016
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
ms.openlocfilehash: cb2bbdb36a102c7ef8974a9ac210473f2306f5d6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746768"
---
# <a name="finally"></a>finally

除了`try`并`catch`子句，CLR 异常处理支持`finally`子句。 与相同的语义是`__finally`阻止在结构化异常处理 (SEH)。 一个`__finally`块可以按照`try`或`catch`块。

## <a name="remarks"></a>备注

用途`finally`块是清理发生异常后继续保持任何资源。 请注意，`finally`始终执行块，即使未引发任何异常。 `catch`引发托管的异常时，仅执行块中关联`try`块。

`finally` 是上下文相关的关键字;请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)有关详细信息。

## <a name="example"></a>示例

下面的示例演示一个简单`finally`块：

```
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

## <a name="see-also"></a>请参阅

[异常处理](../windows/exception-handling-cpp-component-extensions.md)
