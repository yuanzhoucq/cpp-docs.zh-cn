---
title: "noreturn | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "noreturn_cpp"
  - "noreturn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], noreturn"
  - "noreturn __declspec 关键字"
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# noreturn
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 此 `__declspec` 特性告知编译器函数不会返回。  因此，编译器了解到调用 **\_\_declspec\(noreturn\)** 函数后的代码是不可访问的。  
  
 如果编译器找到带有不返回值的控制路径的函数，则它会生成警告 \(C4715\) 或错误消息 \(C2202\)。  如果因一个从不返回的函数导致无法到达控制路径，则可使用 **\_\_declspec\(noreturn\)** 阻止此警告或错误。  
  
> [!NOTE]
>  将 **\_\_declspec\(noreturn\)** 添加到应返回的函数会导致未定义的行为。  
  
## 示例  
 在下面的示例中，**else** 子句不包含 return 语句。将 `fatal` 声明为 **\_\_declspec\(noreturn\)** 可避免错误或警告消息。  
  
```  
// noreturn2.cpp  
__declspec(noreturn) extern void fatal () {}  
  
int main() {  
   if(1)  
     return 1;  
   else if(0)  
     return 0;  
   else  
     fatal();  
}  
```  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)