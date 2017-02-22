---
title: "ConvertBSTRToString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ConvertBSTRToString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ConvertBSTRToString 函数"
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ConvertBSTRToString
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将 `BSTR` 值转换为 **char \***。  
  
## 语法  
  
```  
  
      char* __stdcall ConvertBSTRToString(  
   BSTR pSrc  
);  
```  
  
#### 参数  
 `pSrc`  
 BSTR 变量。  
  
## 备注  
 `ConvertBSTRToString` 分配必须删除的字符串。  
  
## 示例  
  
```  
// ConvertBSTRToString.cpp  
#include <comutil.h>  
#include <stdio.h>  
  
#pragma comment(lib, "comsuppw.lib")  
  
int main() {  
   BSTR bstrText = ::SysAllocString(L"Test");  
   wprintf_s(L"BSTR text: %s\n", bstrText);  
  
   char* lpszText2 = _com_util::ConvertBSTRToString(bstrText);  
   printf_s("char * text: %s\n", lpszText2);  
  
   SysFreeString(bstrText);  
   delete[] lpszText2;  
}  
```  
  
  **BSTR 文本：Test**  
**char \* 文本：Test**   
## 结束 Microsoft 专用  
  
## 要求  
 **标头：**comutil.h。  
  
 **Lib：**comsuppw.lib 或 comsuppwd.lib（有关详细信息，请参阅 [\/Zc:wchar\_t（wchar\_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)）  
  
## 请参阅  
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)