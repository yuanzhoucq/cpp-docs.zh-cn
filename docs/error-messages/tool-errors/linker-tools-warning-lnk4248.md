---
title: 链接器工具警告 LNK4248 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4248
dev_langs:
- C++
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3b67661d1ad260f388f8425420711ae2f708ce3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4248"></a>链接器工具警告 LNK4248
对于 type; 的未解析的 typeref 标记 （令牌）图像可能无法运行  
  
 一种类型在 MSIL 元数据中没有一个定义。  
  
 仅 MSIL 模块中的类型的前向声明时，可能出现 lnk4248 警告 (与编译 **/clr**)、 在 MSIL 模块中，引用类型和 MSIL 模块链接到包含具有定义的本机模块类型。  
  
 在此情况下，链接器将提供 MSIL 元数据中的本机类型定义，这可以提供正确的行为。  
  
 但是，如果转发类型声明为 CLR 类型，则链接器的本机类型定义可能不正确  
  
 有关详细信息，请参阅 [/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  提供的 MSIL 模块中的类型定义。  
  
## <a name="example"></a>示例  
 下面的示例生成 LNK4248。 定义结构 A 若要解决。  
  
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
  
## <a name="example"></a>示例  
 下面的示例已转发的类型的定义。  
  
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
  
## <a name="example"></a>示例  
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