---
title: "_get_purecall_handler _set_purecall_handler | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_purecall_handler"
  - "_set_purecall_handler_m"
  - "_get_purecall_handler"
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
  - "_set_purecall_handler"
  - "_set_purecall_handler_m"
  - "set_purecall_handler_m"
  - "set_purecall_handler"
  - "stdlib/_set_purecall_handler"
  - "stdlib/_get_purecall_handler"
  - "_get_purecall_handler"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_purecall_handler 函数"
  - "set_purecall_handler 函数"
  - "purecall_handler"
  - "set_purecall_handler_m 函数"
  - "_purecall_handler"
  - "_set_purecall_handler_m 函数"
  - "_get_purecall_handler 函数"
ms.assetid: 2759b878-8afa-4129-86e7-72afc2153d9c
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_purecall_handler _set_purecall_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取或设置纯虚函数调用的错误处理程序。  
  
## 语法  
  
```  
typedef void (__cdecl* _purecall_handler)(void);  
  
_purecall_handler __cdecl _get_purecall_handler(void);  
  
_purecall_handler __cdecl _set_purecall_handler(   
   _purecall_handler function  
);  
```  
  
#### 参数  
 `function`  
 要在调用纯虚函数时调用的函数。`_purecall_handler` 函数必须具有 void 返回类型。  
  
## 返回值  
 之前的 `_purecall_handler`。 如果之前的处理程序不存在，则返回 `nullptr`。  
  
## 备注  
 `_get_purecall_handler` 和 `_set_purecall_handler` 函数特定于 Microsoft 的且仅适用于 c \+ \+ 代码。  
  
 对一个纯虚函数的调用是一个错误，因为它不具有实现。 默认情况下，编译器将生成代码来调用错误处理程序函数，当调用纯虚函数时，这将终止该程序。 您可以安装纯虚函数调用，以将其进行调试或报告的数据捕获您自己错误处理程序函数。 若要使用您自己的错误处理程序，创建一个具有函数 `_purecall_handler` 签名，然后使用 `_set_purecall_handler` 以使其当前处理程序。  
  
 因为只有一个 `_purecall_handler` 为每个进程，当您调用 `_set_purecall_handler` 立即会影响所有线程。 任一线程上的最后一个调用方将设置该处理程序。  
  
 若要还原默认行为，请调用 `_set_purecall_handler` 使用 `nullptr` 参数。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_get_purecall_handler`, `_set_purecall_handler`|\< cstdlib \> 或 \< stdlib.h \>|  
  
 有关兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// _set_purecall_handler.cpp  
// compile with: /W1  
#include <tchar.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
class CDerived;  
class CBase  
{  
public:  
   CBase(CDerived *derived): m_pDerived(derived) {};  
   ~CBase();  
   virtual void function(void) = 0;  
  
   CDerived * m_pDerived;  
};  
  
class CDerived : public CBase  
{  
public:  
   CDerived() : CBase(this) {};   // C4355  
   virtual void function(void) {};  
};  
  
CBase::~CBase()  
{  
   m_pDerived -> function();  
}  
  
void myPurecallHandler(void)  
{  
   printf("In _purecall_handler.");  
   exit(0);  
}  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
   _set_purecall_handler(myPurecallHandler);  
   CDerived myDerived;  
}  
```  
  
```Output  
在 _purecall_handler 中。  
```  
  
## 请参阅  
 [错误处理](../../c-runtime-library/error-handling-crt.md)   
 [\_purecall](../../c-runtime-library/reference/purecall.md)