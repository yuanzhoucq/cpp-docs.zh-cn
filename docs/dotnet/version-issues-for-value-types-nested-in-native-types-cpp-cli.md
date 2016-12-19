---
title: "嵌套在本机类型中的值类型的版本问题 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__nogc 类型声明"
  - "__value 关键字, 嵌套时的问题"
ms.assetid: 0a3b1a43-39c6-4b52-be2f-1074690188aa
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 嵌套在本机类型中的值类型的版本问题 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

请考虑用于生成客户端程序集的签名（强名称）程序集组件。  此组件包含一个值类型，该值类型在客户端中用作本机联合、类或数组的成员的类型。  如果此组件的未来版本更改此值类型的大小或布局，则必须重新编译客户端。  
  
 使用 [sn.exe](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) \(`sn -k mykey.snk`\) 创建 keyfile。  
  
## 示例  
 下面的示例为该组件。  
  
```  
// nested_value_types.cpp  
// compile with: /clr /LD  
using namespace System::Reflection;  
[assembly:AssemblyVersion("1.0.0.*"),   
assembly:AssemblyKeyFile("mykey.snk")];  
  
public value struct S {  
   int i;  
   void Test() {  
      System::Console::WriteLine("S.i = {0}", i);  
   }  
};  
```  
  
## 示例  
 下面的示例为该客户端：  
  
```  
// nested_value_types_2.cpp  
// compile with: /clr  
#using <nested_value_types.dll>  
  
struct S2 {  
   S MyS1, MyS2;  
};  
  
int main() {  
   S2 MyS2a, MyS2b;  
   MyS2a.MyS1.i = 5;  
   MyS2a.MyS2.i = 6;  
   MyS2b.MyS1.i = 10;  
   MyS2b.MyS2.i = 11;  
  
   MyS2a.MyS1.Test();  
   MyS2a.MyS2.Test();  
   MyS2b.MyS1.Test();  
   MyS2b.MyS2.Test();  
}  
```  
  
## Output  
  
```  
S.i = 5  
S.i = 6  
S.i = 10  
S.i = 11  
```  
  
### 注释  
 但是，如果向 nested\_value\_types.cpp 中的 `struct S` 添加另一个成员（例如 `double d;`）,并且在不重新编译客户端的情况下重新编译组件，则结果为未经处理的异常（类型为 <xref:System.IO.FileLoadException?displayProperty=fullName>）。  
  
## 请参阅  
 [托管类型](../dotnet/managed-types-cpp-cli.md)