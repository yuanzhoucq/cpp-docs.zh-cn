---
title: "_set_com_error_handler |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 626227fb9c5162e5b9fc72fc64348b75ecb27e44
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

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
 `pHandler`  
 指向替换函数的指针。  
  
 `hr`  
 `HRESULT` 信息。  
  
 `perrinfo`  
 `IErrorInfo` 对象。  
  
## <a name="remarks"></a>备注  
 默认情况下， [_com_raise_error](../cpp/com-raise-error.md)处理所有 COM 错误。 您可以通过使用 `_set_com_error_handler` 调用您自己的错误处理函数来更改此行为。  
  
 替换函数必须具有与 `_com_raise_error` 的签名等效的签名。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
Exception raised: Unable to establish the connection!  
```  
  
## <a name="requirements"></a>要求  
 **标头：** comdef.h  
  
 **Lib:**如果**wchar_t is Native Type**编译器选项设置为 on，请使用对 comsuppw.lib 或 comsuppwd.lib。 如果**wchar_t is Native Type** ，请使用 comsupp.lib。 有关详细信息，请参阅 [/Zc:wchar_t（wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
## <a name="see-also"></a>另请参阅  
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)
