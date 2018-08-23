---
title: 最后 |Microsoft 文档
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
ms.openlocfilehash: 70057cad8ff5bca0606f06dd43eaa485834d2c70
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111466"
---
# <a name="finally"></a>finally
除了`try`和`catch`子句，CLR 异常处理支持`finally`子句。 语义相等`__finally`块中，在结构化异常处理 (SEH)。 A`__finally`块可以按照`try`或`catch`块。  
  
## <a name="remarks"></a>备注  
 用途`finally`块是清理任何资源保留在发生异常。 请注意，`finally`始终执行块，即使没有引发异常。 `catch`如果引发托管的异常，则仅执行块内关联`try`块。  
  
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