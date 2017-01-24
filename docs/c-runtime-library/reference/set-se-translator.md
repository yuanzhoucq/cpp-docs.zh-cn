---
title: "_set_se_translator | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_se_translator"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_set_se_translator"
  - "set_se_translator"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_se_translator 函数"
  - "异常处理, 更改"
  - "set_se_translator 函数"
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_se_translator
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

处理作为 C\+\+ 键入异常的 Win32 异常 \(C 结构化异常\) 。  
  
## 语法  
  
```  
_se_translator_function _set_se_translator(  
   _se_translator_function seTransFunction  
);  
```  
  
#### 参数  
 `seTransFunction`  
 指向您编写的C结构化异常转换器函数的指针。  
  
## 返回值  
 返回指向由 `_set_se_translator` 注册的前终端转换函数，以便前面的函数之后可能还原。  如果以前尚未设置函数，返回值可用于存储默认行为；此值可能为 NULL。  
  
## 备注  
 `_set_se_translator` 函数提供一种方法处理 Win32异常 \(C\# 结构化异常\) 作为 C\+\+ 类型的异常。  若要允许每个异常由C\+\+ `catch` 处理程序处理，请首先定义一个可用的C异常包装类，或者为指定的类传递C异常。。  若要使用此类，请安装 C 异常时由内部异常处理机制调用的自定义 C 异常转换函数。  在转换器函数内，则可以引发通过匹配 C\+\+ `catch` 处理程序捕捉的任何类型化异常。  
  
 在使用 `_set_se_translator`时，必须使用。[\/EHa](../../build/reference/eh-exception-handling-model.md)  
  
 若要指定自定义转换函数，请使用您的转换函数的名称作为`_set_se_translator`  的单一参数来调用它。  您编写的转换函数对具有`try`  块的堆栈上的每个函数调用一次。  无默认转换器函数。  
  
 转换器函数应执行不多于引发 C\+\+ 类型异常。  如果它进行任何操作除了引发。例如 \(如写入日志文件\)，程序可能不会以预期，转换器，因为函数调用的次数与平台依赖项。  
  
 在多线程环境中，每个线程都是单独维护转换函数。  每个新线程需要安装自己的转换函数。  因此，每个线程都控制自己终转换处理。  `_set_se_translator` 特定于一个线程；另一个 DLL 来安装不同的转换函数。  
  
 您编写的是本机 `seTransFunction` 函数必须编译的函数 \(不使用 \/clr 编译。\)。  它必须采用无符号整数和指针到 Win32 `_EXCEPTION_POINTERS` 结构作为参数。  参数分别返回值调用 Win32 API `GetExceptionCode` 和 `GetExceptionInformation` 函数。  
  
```  
typedef void (*_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );  
```  
  
 对于 `_set_se_translator`，即，在动态链接到 CRT，有问题；在进程的其他 DLL 可能调用 `_set_se_translator` 并用自己替换处理程序。  
  
 在使用从托管代码的 `_set_se_translator` 编译代码 \(使用 \/clr\) 或混合本机代码和托管代码，请注意类型影响仅在本机代码生成的异常。  托管代码生成的任何托管异常 \(例如，当 `System::Exception`引发\) 时不是通过函数转换器进行路由。  如下一个将的系统异常引发托管代码使用 Win32 函数 `RaiseException` 或引发的异常由零的异常在转换器进行路由。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_set_se_translator`|\<eh.h\>|  
  
 `_set_se_translator` 提供的功能不可用代码编译的编译器选项。[\/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_settrans.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <windows.h>  
#include <eh.h>  
  
void SEFunc();  
void trans_func( unsigned int, EXCEPTION_POINTERS* );  
  
class SE_Exception  
{  
private:  
    unsigned int nSE;  
public:  
    SE_Exception() {}  
    SE_Exception( unsigned int n ) : nSE( n ) {}  
    ~SE_Exception() {}  
    unsigned int getSeNumber() { return nSE; }  
};  
int main( void )  
{  
    try  
    {  
        _set_se_translator( trans_func );  
        SEFunc();  
    }  
    catch( SE_Exception e )  
    {  
        printf( "Caught a __try exception with SE_Exception.\n" );  
    }  
}  
void SEFunc()  
{  
    __try  
    {  
        int x, y=0;  
        x = 5 / y;  
    }  
    __finally  
    {  
        printf( "In finally\n" );  
    }  
}  
void trans_func( unsigned int u, EXCEPTION_POINTERS* pExp )  
{  
    printf( "In trans_func.\n" );  
    throw SE_Exception();  
}  
```  
  
  **In trans\_func.**  
**In finally**  
**Caught a \_\_try exception with SE\_Exception.**   
## 示例  
 虽然 `_set_se_translator` 提供的功能不可用。托管代码，此映射在本机代码是可以的，因此，即使该本机代码中编译。`/clr` 开关下，使用 `#pragma unmanaged`，因此，只要指示本机代码。  如果结构化异常引发。要映射的托管代码，必须生成标记的代码为 `pragma`和处理异常。  下面的代码演示可能的用途。  有关详细信息，请参阅[Pragma 指令和 \_\_Pragma 关键字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。  
  
```  
// crt_set_se_translator_clr.cpp  
// compile with: /clr  
#include <windows.h>  
#include <eh.h>  
#include <assert.h>  
#include <stdio.h>  
  
int thrower_func(int i) {  
   int j = i/0;  
  return 0;  
}  
  
class CMyException{  
};  
  
#pragma unmanaged  
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS pExp )  
{  
printf("Translating the structured exception to a C++"  
             " exception.\n");  
throw CMyException();  
}  
  
void DoTest()  
{  
    try  
    {  
      thrower_func(10);  
    }   
  
    catch(CMyException e)  
    {  
printf("Caught CMyException.\n");  
    }  
    catch(...)  
    {  
      printf("Caught unexpected SEH exception.\n");  
    }  
}  
#pragma managed  
  
int main(int argc, char** argv) {  
    _set_se_translator(my_trans_func);  
    DoTest();  
    return 0;  
}  
```  
  
  **转换为 C. 异常和结构化异常。**  
**捕获的 CMyException。**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [异常处理例程](../../c-runtime-library/exception-handling-routines.md)   
 [set\_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [set\_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [terminate](../../c-runtime-library/reference/terminate-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)