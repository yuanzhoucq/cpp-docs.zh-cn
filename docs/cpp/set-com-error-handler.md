---
title: _set_com_error_handler |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08d5df7893aa5390a6e577e3c26424864f7c3a8f
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465761"
---
# <a name="setcomerrorhandler"></a>_set_com_error_handler
**Microsoft 专用**  
  
 替换用于 COM 错误处理的默认函数。  
  
## <a name="syntax"></a>语法  
  
```  
void __stdcall _set_com_error_handler(  
   void (__stdcall *pHandler)(  
      HRESULT hr,   
      IErrorInfo* perrinfo  
   )  
);  
```  
  
#### <a name="parameters"></a>参数  
 *pHandler*  
 指向替换函数的指针。  
  
 *hr*  
 HRESULT 的信息。  
  
 *perrinfo*  
 `IErrorInfo` 对象。  
  
## <a name="remarks"></a>备注  
 默认情况下[_com_raise_error](../cpp/com-raise-error.md)处理所有 COM 错误。 可以通过更改此行为 **_set_com_error_handler**调用错误处理函数。  
  
 替换函数必须具有与 `_com_raise_error` 的签名等效的签名。  
  
## <a name="example"></a>示例  
  
```cpp 
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
  
```Output  
Exception raised: Unable to establish the connection!  
```  
  
## <a name="requirements"></a>要求  
 **标头：** \<comdef.h >  
  
 **Lib:** 如果**wchar_t 是本机类型**编译器选项已打开，请使用 comsuppw.lib 或 comsuppwd.lib。 如果**wchar_t 是本机类型**未启用，请使用 comsupp.lib。 有关详细信息，请参阅 [/Zc:wchar_t（wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
## <a name="see-also"></a>请参阅  
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)