---
title: "链接器工具错误 LNK2031 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2031"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2031"
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 链接器工具错误 LNK2031
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法为“function\_declaration”修饰名生成 p\/invoke；元数据中缺少调用约定  
  
 在尝试将本机函数导入到纯映像中时，请谨记隐式调用约定在本机编译和纯编译间的差异。  有关纯映像的更多信息，请参见[纯代码和可验证代码](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
## 示例  
 此代码示例用导出的本机函数生成一个组件，该函数的调用约定为隐式 [\_\_cdecl](../../cpp/cdecl.md)。  
  
```  
// LNK2031.cpp  
// compile with: /LD  
extern "C" {  
   __declspec(dllexport) int func() { return 3; }  
};  
```  
  
## 示例  
 下面的示例创建一个使用本机函数的纯客户端。  但是，**\/clr:pure** 下的调用约定为 [\_\_clrcall](../../cpp/clrcall.md)。  以下示例将生成 LNK2031：  
  
```  
// LNK2031_b.cpp  
// compile with: /clr:pure LNK2031.lib  
// LNK2031 expected  
extern "C" int func();  
  
int main() {  
   return func();  
}  
```  
  
## 示例  
 以下示例将演示如何使用纯映像中的本机函数。  注意显式 **\_\_cdecl** 调用约定说明符。  
  
```  
// LNK2031_c.cpp  
// compile with: /clr:pure LNK2031.lib  
extern "C" int __cdecl func();  
  
int main() {  
   return func();  
}  
```