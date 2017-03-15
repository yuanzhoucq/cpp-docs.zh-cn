---
title: "/CLR 下的异常处理行为的差异 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EXCEPTION_CONTINUE_EXECUTION 宏"
  - "set_se_translator 函数"
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# /CLR 下的异常处理行为的差异
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[使用托管异常中的基本概念](../dotnet/basic-concepts-in-using-managed-exceptions.md) 在托管应用程序中讨论异常处理。  在本主题中，从标准行为的不同处理异常和限制一些详细讨论。  有关 SE 转换函数的更多信息，请参见 [\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md)。  
  
##  <a name="vcconjumpingoutofafinallyblock"></a> Finally 块跳出  
 在本机 C\/C\+\+ 代码，跳出**finally** 块使用结构化异常处理，但允许 \(SEH\) 将产生警告。在 [\/clr](../build/reference/clr-common-language-runtime-compilation.md)下，跳出 **finally** 块产生错误：  
  
```  
// clr_exception_handling_4.cpp  
// compile with: /clr  
int main() {  
   try {}  
   finally {  
      return 0;   // also fails with goto, break, continue  
    }  
}   // C3276  
```  
  
##  <a name="vcconraisingexceptionswithinanexceptionfilter"></a> 引发在异常筛选器中的异常  
 当一个异常被引发时 [异常筛选器](../cpp/writing-an-exception-filter.md) 在托管的代码中，异常被捕获并当做筛选器返回了0值。  
  
 这与产生嵌入的异常的本机代码的行为是相反的**EXCEPTION\_RECORD** 结构的 **ExceptionRecord** 字段和 **ExceptionFlags** 字段返回 \(如 [GetExceptionInformation](http://msdn.microsoft.com/library/windows/desktop/ms679357)\) 设置集使用位。  下面的示例中阐释了这种差异。  
  
```  
// clr_exception_handling_5.cpp  
#include <windows.h>  
#include <stdio.h>  
#include <assert.h>  
  
#ifndef false  
#define false 0  
#endif  
  
int *p;  
  
int filter(PEXCEPTION_POINTERS ExceptionPointers) {  
   PEXCEPTION_RECORD ExceptionRecord =   
                     ExceptionPointers->ExceptionRecord;  
  
   if ((ExceptionRecord->ExceptionFlags & 0x10) == 0) {  
      // not a nested exception, throw one  
      *p = 0; // throw another AV  
   }  
   else {  
      printf("Caught a nested exception\n");  
      return 1;  
    }  
  
   assert(false);  
  
   return 0;  
}  
  
void f(void) {  
   __try {  
      *p = 0;   // throw an AV  
   }  
   __except(filter(GetExceptionInformation())) {  
      printf_s("We should execute this handler if "  
                 "compiled to native\n");  
    }  
}  
  
int main() {  
   __try {  
      f();  
   }  
   __except(1) {  
      printf_s("The handler in main caught the "  
               "exception\n");  
    }  
}  
```  
  
### Output  
  
```  
Caught a nested exception  
We should execute this handler if compiled to native  
```  
  
##  <a name="vccondisassociatedrethrows"></a> 分离的 Rethrows  
 **\/clr** 不支持在 catch 处理程序外再次引发该异常 \(这被称为分离的再次引发。\)  此类型异常视为一标准 C\+\+ 异常的再次引发。  如果已分离的再次引发，遇到活动的托管异常时，异常包装为 C.C\+\+ 异常然后再次引发。  此此类型异常只能作为异常[System::SEHException被](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx)被捕获  
  
 以下示例演示托管异常重抛出为C\+\+ 异常：  
  
```  
// clr_exception_handling_6.cpp  
// compile with: /clr  
using namespace System;  
#include <assert.h>  
#include <stdio.h>  
  
void rethrow( void ) {  
   // This rethrow is a dissasociated rethrow.  
   // The exception would be masked as SEHException.  
   throw;  
}  
  
int main() {  
   try {  
      try {  
         throw gcnew ApplicationException;  
      }  
      catch ( ApplicationException^ ) {  
         rethrow();  
         // If the call to rethrow() is replaced with  
         // a throw statement within the catch handler,  
         // the rethrow would be a managed rethrow and  
         // the exception type would remain   
         // System::ApplicationException  
      }  
   }  
  
    catch ( ApplicationException^ ) {  
      assert( false );  
  
      // This will not be executed since the exception  
      // will be masked as SEHException.  
    }  
   catch ( Runtime::InteropServices::SEHException^ ) {  
      printf_s("caught an SEH Exception\n" );  
    }  
}  
```  
  
### Output  
  
```  
caught an SEH Exception  
```  
  
##  <a name="vcconexceptionfiltersandexception_continue_execution"></a> EXCEPTION\_CONTINUE\_EXECUTION \(–1\)  异常消除。  
 如果筛选器在托管应用程序中返回 `EXCEPTION_CONTINUE_EXECUTION`，它将被视作返回了 `EXCEPTION_CONTINUE_SEARCH` 有关这些常量的更多信息，请参见 [try\-except语句](../cpp/try-except-statement.md)。  
  
 下面的示例展示了这一主要差异。  
  
```  
// clr_exception_handling_7.cpp  
#include <windows.h>  
#include <stdio.h>  
#include <assert.h>  
  
int main() {  
   int Counter = 0;  
   __try {  
      __try  {  
         Counter -= 1;  
         RaiseException (0xe0000000|'seh',  
                         0, 0, 0);  
         Counter -= 2;  
      }  
      __except (Counter) {  
         // Counter is negative,  
         // indicating "CONTINUE EXECUTE"  
         Counter -= 1;  
      }  
    }  
    __except(1) {  
      Counter -= 100;  
   }  
  
   printf_s("Counter=%d\n", Counter);  
}  
```  
  
### Output  
  
```  
Counter=-3  
```  
  
##  <a name="vcconthe_set_se_translatorfunction"></a> 函数\_set\_se\_translator  
 转换器函数，通过调用`_set_se_translator`来设置，仅仅会影响非托管代码中的catches。  以下示例展示了这一限制：  
  
```  
// clr_exception_handling_8.cpp  
// compile with: /clr /EHa  
#include <iostream>  
#include <windows.h>  
#include <eh.h>  
#pragma warning (disable: 4101)  
using namespace std;  
using namespace System;  
  
#define MYEXCEPTION_CODE 0xe0000101  
  
class CMyException {  
public:  
   unsigned int m_ErrorCode;  
   EXCEPTION_POINTERS * m_pExp;  
  
   CMyException() : m_ErrorCode( 0 ), m_pExp( NULL ) {}  
  
   CMyException( unsigned int i, EXCEPTION_POINTERS * pExp )  
         : m_ErrorCode( i ), m_pExp( pExp ) {}  
  
   CMyException( CMyException& c ) : m_ErrorCode( c.m_ErrorCode ),  
                                      m_pExp( c.m_pExp ) {}  
  
   friend ostream& operator <<   
                 ( ostream& out, const CMyException& inst ) {  
      return out <<  "CMyException[\n" <<    
             "Error Code: " << inst.m_ErrorCode <<  "]";  
    }  
};  
  
#pragma unmanaged   
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS pExp ) {  
   cout <<  "In my_trans_func.\n";  
   throw CMyException( u, pExp );  
}  
  
#pragma managed   
void managed_func() {  
   try  {  
      RaiseException( MYEXCEPTION_CODE, 0, 0, 0 );  
   }  
   catch ( CMyException x ) {}  
   catch ( ... ) {  
      printf_s("This is invoked since "  
               "_set_se_translator is not "  
               "supported when /clr is used\n" );  
    }  
}  
  
#pragma unmanaged   
void unmanaged_func() {  
   try  {  
      RaiseException( MYEXCEPTION_CODE,   
                      0, 0, 0 );  
   }  
   catch ( CMyException x ) {  
      printf("Caught an SEH exception with "  
             "exception code: %x\n", x.m_ErrorCode );  
    }  
    catch ( ... ) {}  
}  
  
// #pragma managed   
int main( int argc, char ** argv ) {  
   _set_se_translator( my_trans_func );  
  
   // It does not matter whether the translator function  
   // is registered in managed or unmanaged code  
   managed_func();  
   unmanaged_func();  
}  
```  
  
### Output  
  
```  
This is invoked since _set_se_translator is not supported when /clr is used  
In my_trans_func.  
Caught an SEH exception with exception code: e0000101  
```  
  
## 请参阅  
 [异常处理](../windows/exception-handling-cpp-component-extensions.md)   
 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [异常处理](../cpp/exception-handling-in-visual-cpp.md)