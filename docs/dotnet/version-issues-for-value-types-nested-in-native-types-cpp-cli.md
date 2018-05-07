---
title: 值类型的版本问题嵌套在本机类型 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __nogc type declarations
- __value keyword, issues when nesting
ms.assetid: 0a3b1a43-39c6-4b52-be2f-1074690188aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4c4f2598594930f49c1217c937c9142b3f84a47e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="version-issues-for-value-types-nested-in-native-types-ccli"></a>嵌套在本机类型中的值类型的版本问题 (C++/CLI)
请考虑用于生成客户端程序集的签名 （强名称） 程序集组件。 组件包含用于在客户端作为类型的本机联合、 类或数组成员的值类型。 如果该组件的将来版本发生更改的大小或值类型的布局，则客户端必须重新编译。  
  
 创建与 keyfile [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`)。  
  
## <a name="example"></a>示例  
 下面的示例是组件。  
  
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
  
## <a name="example"></a>示例  
 此示例是客户端：  
  
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
  
## <a name="output"></a>输出  
  
```  
S.i = 5  
S.i = 6  
S.i = 10  
S.i = 11  
```  
  
### <a name="comments"></a>注释  
 但是，如果添加到另一个成员`struct S`nested_value_types.cpp 中, (例如， `double d;`) 和无需重新编译客户端重新编译该组件，则结果为未经处理的异常 (类型的<xref:System.IO.FileLoadException?displayProperty=fullName>)。  
  
## <a name="see-also"></a>请参阅  
 [托管类型 (C++/CLI)](../dotnet/managed-types-cpp-cli.md)