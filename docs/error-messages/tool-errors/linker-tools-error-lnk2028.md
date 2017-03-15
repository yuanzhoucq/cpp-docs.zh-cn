---
title: "链接器工具错误 LNK2028 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2028"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2028"
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 链接器工具错误 LNK2028
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“exported\_function”\(decorated\_name\) 在函数“function\_containing\_function\_call”\(decorated\_name\) 中被引用  
  
 在尝试将本机函数导入到纯映像中时，请谨记隐式调用约定在本机编译和纯编译间的差异。  
  
## 示例  
 此代码示例用导出的本机函数生成一个组件，该函数的调用约定为隐式 [\_\_cdecl](../../cpp/cdecl.md)。  
  
```  
// LNK2028.cpp  
// compile with: /LD  
__declspec(dllexport) int func() {  
   return 3;  
}  
```  
  
## 示例  
 下面的示例创建一个使用本机函数的纯客户端。  但是，**\/clr:pure** 下的调用约定为 [\_\_clrcall](../../cpp/clrcall.md)。  下面的示例生成 LNK2028。  
  
```  
// LNK2028_b.cpp  
// compile with: /clr:pure lnk2028.lib  
// LNK2028 expected  
int func();  
  
int main() {  
   return func();  
}  
```