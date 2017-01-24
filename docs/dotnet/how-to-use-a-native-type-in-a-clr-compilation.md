---
title: "如何：在 /clr 编译中使用本机类型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 编译器选项 [C++], 使用本机类型"
  - "编译, /clr 中的本机类型"
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 /clr 编译中使用本机类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以在 **\/clr** 编译中定义本机类型，并且从程序集内部对该本机类型的任何使用都是有效的。  但是，本机类型从引用的元数据中将不可用。  
  
 每个程序集必须包含它将使用的各个本机类型的定义。  
  
 有关详细信息，请参阅[\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 示例  
 此示例创建一个定义和使用本机类型的组件。  
  
```  
// use_native_type_in_clr.cpp  
// compile with: /clr /LD  
public struct NativeClass {  
   static int Test() { return 98; }  
};  
  
public ref struct ManagedClass {  
   static int i = NativeClass::Test();  
   void Test() {  
      System::Console::WriteLine(i);  
   }  
};  
```  
  
## 示例  
 此示例定义一个使用此组件的客户端。  请注意，访问本机类型是错误的，除非在 compiland 中定义了它。  
  
```  
// use_native_type_in_clr_2.cpp  
// compile with: /clr  
#using "use_native_type_in_clr.dll"  
// Uncomment the following 3 lines to resolve.  
// public struct NativeClass {  
//    static int Test() { return 98; }  
// };  
  
int main() {  
   ManagedClass x;  
   x.Test();  
  
   System::Console::WriteLine(NativeClass::Test());   // C2653  
}  
```  
  
## 请参阅  
 [使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)