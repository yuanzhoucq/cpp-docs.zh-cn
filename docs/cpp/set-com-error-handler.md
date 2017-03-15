---
title: "_set_com_error_handler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_set_com_error_handler 函数"
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# _set_com_error_handler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 替换用于 COM 错误处理的默认函数。  
  
## 语法  
  
```  
void __stdcall _set_com_error_handler(  
   void (__stdcall *pHandler)(  
      HRESULT hr,   
      IErrorInfo* perrinfo  
   )  
);  
```  
  
#### 参数  
 `pHandler`  
 指向替换函数的指针。  
  
 `hr`  
 `HRESULT` 信息。  
  
 `perrinfo`  
 `IErrorInfo` 对象。  
  
## 备注  
 默认情况下，[\_com\_raise\_error](../cpp/com-raise-error.md) 处理所有 COM 错误。  您可以通过使用 `_set_com_error_handler` 调用您自己的错误处理函数来更改此行为。  
  
 替换函数必须具有与 `_com_raise_error` 的签名等效的签名。  
  
## 示例  
  
```  
// _set_com_error_handler.cpp  
// compile with /EHsc  
#include <stdio.h>  
#include <comdef.h>  
#include <comutil.h>  
  
// Importing ado dll to attempt to establish an ado connection.  
// Not related to _set_com_error_handler   
#import "C:\Program Files\Common Files\System\ado\msado15.dll" no_namespace rename("EOF", "adoEOF")  
  
void __stdcall _My_com_raise_error(HRESULT hr, IErrorInfo* perrinfo)  
{  
   throw "Unable to establish the connection!";  
}  
  
int main()  
{  
   _set_com_error_handler(_My_com_raise_error);  
   _bstr_t bstrEmpty(L"");  
   _ConnectionPtr Connection = NULL;  
   try  
   {  
      Connection.CreateInstance(__uuidof(Connection));  
      Connection->Open(bstrEmpty, bstrEmpty, bstrEmpty, 0);   
   }  
   catch(char* errorMessage)  
   {  
      printf("Exception raised: %s\n", errorMessage);  
   }  
  
   return 0;  
}  
```  
  
  **引发的异常：无法建立连接！**   
## 要求  
 **标头：**comdef.h  
  
 **库：**如果启用“wchar\_t is Native Type”编译器选项，请使用 comsuppw.lib 或 comsuppwd.lib。  如果禁用“wchar\_t is Native Type”，请使用 comsupp.lib。  有关详细信息，请参阅 [\/Zc:wchar\_t（wchar\_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
## 请参阅  
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)