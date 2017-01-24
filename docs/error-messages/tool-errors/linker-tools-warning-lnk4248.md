---
title: "链接器工具警告 LNK4248 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4248"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4248"
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4248
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

‘type’的 typeref 标记 \(token\) 无法解析；映像可能无法运行  
  
 在 MSIL 元数据中不存在类型的定义。  
  
 在 MSIL 模块中引用类型时，如果 MSIL 模块链接到包含某类型的定义的本机模块，但 MSIL 模块中却只有该类型的前向声明（使用 **\/clr** 编译），便可能出现 LNK4248 警告。  
  
 在这种情况下，链接器将在 MSIL 元数据中提供本机类型定义，这可规定正确的行为。  
  
 但是，如果前向类型声明为 CLR 类型，链接器的本机类型定义则可能不正确。  
  
 有关详细信息，请参阅[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### 更正此错误  
  
1.  在 MSIL 模块中提供类型定义。  
  
## 示例  
 下面的示例生成 LNK4248。  定义要解析的结构 A。  
  
```  
// LNK4248.cpp  
// compile with: /clr /W1  
// LNK4248 expected  
struct A;  
void Test(A*){}  
  
int main() {  
   Test(0);  
}  
```  
  
## 示例  
 下面的示例具有类型的前向定义。  
  
```  
// LNK4248_2.cpp  
// compile with: /clr /c  
class A;   // provide a definition for A here to resolve  
A * newA();  
int valueA(A * a);  
  
int main() {  
   A * a = newA();  
   return valueA(a);  
}  
```  
  
## 示例  
 下面的示例生成 LNK4248。  
  
```  
// LNK4248_3.cpp  
// compile with: /c  
// post-build command: link LNK4248_2.obj LNK4248_3.obj  
class A {  
public:   
   int b;  
};  
  
A* newA() {  
   return new A;  
}  
  
int valueA(A * a) {  
   return (int)a;  
}  
```