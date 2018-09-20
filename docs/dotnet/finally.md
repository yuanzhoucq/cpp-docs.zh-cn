---
title: 最后 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- finally keyword [C++]
ms.assetid: b55f3c8e-1af0-43e8-bcfb-99c3685d2578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 818ee6736d51303b047cb5a47aae02441557db29
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447268"
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