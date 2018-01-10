---
title: "ConvertStringToBSTR |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ConvertStringToBSTR
dev_langs: C++
helpviewer_keywords: ConvertStringToBSTR function
ms.assetid: 071f9b3b-9643-4e06-a1e5-de96ed15bab2
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4347fdcf25373e088a8d8bc54cc3219285aa347
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="convertstringtobstr"></a>ConvertStringToBSTR
**Microsoft 专用**  
  
 将转换**char \*** 值赋给`BSTR`。  
  
## <a name="syntax"></a>语法  
  
```  
  
      BSTR __stdcall ConvertStringToBSTR(  
   const char* pSrc  
)  
```  
  
#### <a name="parameters"></a>参数  
 `pSrc`  
 A **char \*** 变量。  
  
## <a name="example"></a>示例  
  
```  
// ConvertStringToBSTR.cpp  
#include <comutil.h>  
#include <stdio.h>  
  
#pragma comment(lib, "comsuppw.lib")  
#pragma comment(lib, "kernel32.lib")  
  
int main() {  
   char* lpszText = "Test";  
   printf_s("char * text: %s\n", lpszText);  
  
   BSTR bstrText = _com_util::ConvertStringToBSTR(lpszText);  
   wprintf_s(L"BSTR text: %s\n", bstrText);  
  
   SysFreeString(bstrText);  
}  
```  
  
```Output  
char * text: Test  
BSTR text: Test  
```  
  
**结束 Microsoft 专用**  
  
## <a name="requirements"></a>惠?  
 **标头：** comutil.h  
  
 **Lib:**对 comsuppw.lib 或 comsuppwd.lib (请参阅[/zc: wchar_t （wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)有关详细信息)  
  
## <a name="see-also"></a>请参阅  
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)