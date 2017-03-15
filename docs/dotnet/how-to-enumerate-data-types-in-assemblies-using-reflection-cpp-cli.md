---
title: "如何：使用反射枚举程序集中的数据类型 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "程序集 [C++]"
  - "程序集 [C++], 枚举数据类型"
  - "数据类型 [C++], 枚举"
  - "公共成员 [C++]"
  - "公共类型 [C++]"
  - "反射 [C++], 外部程序集"
ms.assetid: c3578e6d-bb99-4599-80e1-ab795305f878
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用反射枚举程序集中的数据类型 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的代码演示如何使用 <xref:System.Reflection> 枚举公共类型和成员。  
  
 如果在本地目录或 GAC 中给出程序集的名称，下面的代码将尝试打开该程序集并检索说明。  如果成功，将显示每个类型及其公共成员。  
  
 请注意，<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 要求不使用文件扩展名。  因此，使用“mscorlib.dll”作为命令行参数时将会失败，而只使用“mscorlib”则会显示 .NET Framework 类型。  如果未提供程序集名称，代码将检测并报告当前程序集内的类型（由此代码生成的 EXE）。  
  
## 示例  
  
```  
// self_reflection.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Reflection;  
using namespace System::Collections;  
  
public ref class ExampleType {  
public:  
   ExampleType() {}  
   void Func() {}  
};  
  
int main() {  
   String^ delimStr = " ";  
   array<Char>^ delimiter = delimStr->ToCharArray( );  
   array<String^>^ args = Environment::CommandLine->Split( delimiter );  
  
// replace "self_reflection.exe" with an assembly from either the local  
// directory or the GAC  
   Assembly^ a = Assembly::LoadFrom("self_reflection.exe");  
   Console::WriteLine(a);  
  
   int count = 0;  
   array<Type^>^ types = a->GetTypes();  
   IEnumerator^ typeIter = types->GetEnumerator();  
  
   while ( typeIter->MoveNext() ) {  
      Type^ t = dynamic_cast<Type^>(typeIter->Current);  
      Console::WriteLine("   {0}", t->ToString());  
  
      array<MemberInfo^>^ members = t->GetMembers();  
      IEnumerator^ memberIter = members->GetEnumerator();  
      while ( memberIter->MoveNext() ) {  
         MemberInfo^ mi = dynamic_cast<MemberInfo^>(memberIter->Current);  
         Console::Write("      {0}", mi->ToString( ) );  
         if (mi->MemberType == MemberTypes::Constructor)  
            Console::Write("   (constructor)");  
  
         Console::WriteLine();  
      }  
      count++;  
   }  
   Console::WriteLine("{0} types found", count);  
}  
```  
  
## 请参阅  
 [反射](../dotnet/reflection-cpp-cli.md)