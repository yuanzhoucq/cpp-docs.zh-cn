---
title: "ConvertStringToBSTR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ConvertStringToBSTR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ConvertStringToBSTR 函数"
ms.assetid: 071f9b3b-9643-4e06-a1e5-de96ed15bab2
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ConvertStringToBSTR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将 **char \*** 值转换为 `BSTR`。  
  
## 语法  
  
```  
  
      BSTR __stdcall ConvertStringToBSTR(  
   const char* pSrc  
)  
```  
  
#### 参数  
 `pSrc`  
 **char \*** 变量。  
  
## 示例  
  
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
  
  **char \* 文本：Test**  
**BSTR 文本：Test**   
## 结束 Microsoft 专用  
  
## 要求  
 **头文件：** comutil.h  
  
 **Lib：**comsuppw.lib 或 comsuppwd.lib（有关详细信息，请参阅 [\/Zc:wchar\_t（wchar\_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)）  
  
## 请参阅  
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)