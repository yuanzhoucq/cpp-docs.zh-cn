---
title: "友元程序集 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "友元程序集，Visual C++"
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 友元程序集 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

适当的运行时，则友元 *程序集* 语言功能将在命名空间范围或全局范围的程序集中的组件可访问一个或多个客户程序集或 .netmodules 的类型。  
  
## 所有运行时  
 **备注**  
  
 （此语言在中任何没有运行时支持。）  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **备注**  
  
 \(此语言功能在[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]中不支持。\)  
  
### 要求  
 编译器选项：**\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **备注**  
  
#### 使类型在命名空间范围或全局范围，程序集可以访问客户 .netmodule 程序集或组件  
  
1.  在组件中指定程序集特性 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>，而将访问类型在命名空间范围或全局范围。客户组件程序集或 .netmodule 的名称。通过指定附加的特性指定多客户端程序集或 .netmodules。  
  
2.  在客户端程序集或 .netmodule，使用 `#using`时，当您引用组件程序集，请将 `as_friend` 特性。如果对未指定 `InternalsVisibleToAttribute`的程序集指定 `as_friend` 特性，则运行时将引发异常，如果尝试访问类型在命名空间范围或全局范围中的组件。  
  
 如果包含 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 特性的程序集没有强名称将产生一个错误，，则程序集使用 `as_friend` 特性中的客户。  
  
 虽然在命名空间范围和全局范围的类型可以为客户端程序集或 .netmodule 已知，成员可访问性仍然有效。例如，您无法访问私有成员。  
  
 添加整访问程序集中必须显式授予。例如，C 不能访问的任何程序集输入程序集 A，如果程序集 C 引用了程序集 B，而将访问的所有程序集输入程序集 A。  
  
 有关如何指定类型的可访问性的信息在程序集外，请参见 [类型可见性](../misc/type-visibility.md)。  
  
 有关对符号是使用 Visual C\+\+ 编译器，如何为对生成程序集的强名称信息的方式，请参见 [强名称程序集（程序集签名）](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
 用于友元程序集的功能，您的重写都使用 <xref:System.Security.Permissions.StrongNameIdentityPermission> 限制对各个类型的访问权限。  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 下面的代码示例定义了指定客户端程序集可以访问该类型在组件的组件。  
  
```  
// friend_assemblies.cpp  
// compile by using: /clr /LD  
using namespace System::Runtime::CompilerServices;  
using namespace System;  
// an assembly attribute, not bound to a type  
[assembly:InternalsVisibleTo("friend_assemblies_2")];  
  
ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 下面的代码示例访问私有类型组件。  
  
```  
// friend_assemblies_2.cpp  
// compile by using: /clr  
#using "friend_assemblies.dll" as_friend  
  
int main() {  
   Class1 ^ a = gcnew Class1;  
   a->Test_Public();  
}  
```  
  
 **Output**  
  
 `Class1::Test_Public`  
  
 下面的代码示例定义了一个组件，但没有指定将对类型的在组件的客户程序集。  
  
 请注意，使用 **\/opt:noref**组件链接。  这确保私有类型的组件元数据发出，不需要 `InternalsVisibleTo` 时，特性存在。  有关详细信息，请参阅[\/OPT（优化）](../build/reference/opt-optimizations.md)。  
  
```  
// friend_assemblies_3.cpp  
// compile by using: /clr /LD /link /opt:noref  
using namespace System;  
  
ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 下面的代码示例定义访问专用的组件尝试输入不允许访问其私有类型的访问的客户。  由于运行时的行为，如果您为了捕捉异常，则必须访问私有类型尝试帮助器函数。  
  
```  
// friend_assemblies_4.cpp  
// compile by using: /clr  
#using "friend_assemblies_3.dll" as_friend  
using namespace System;  
  
void Test() {  
   Class1 ^ a = gcnew Class1;  
}  
  
int main() {  
   // to catch this kind of exception, use a helper function  
   try {  
      Test();     
   }  
   catch(MethodAccessException ^ e) {  
      Console::WriteLine("caught an exception");  
   }  
}  
```  
  
 **Output**  
  
 `caught an exception`  
  
 下面的代码示例演示如何创建一客户端程序集可以访问该类型在组件的强名称组件。  
  
```  
// friend_assemblies_5.cpp  
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk  
using namespace System::Runtime::CompilerServices;  
using namespace System;  
// an assembly attribute, not bound to a type  
  
[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];  
  
private ref class Class1 {  
public:  
   void Test_Public() {  
      Console::WriteLine("Class1::Test_Public");  
   }  
};  
```  
  
 注意必须组件指定其公钥。  我们建议您按顺序运行以下命令在命令提示符处创建密钥对并获取公钥：  
  
 **sn \-d friend\_assemblies.snk**  
  
 **sn \-k friend\_assemblies.snk**  
  
 **sn \-i friend\_assemblies.snk friend\_assemblies.snk**  
  
 **sn \-pc friend\_assemblies.snk key.publickey**  
  
 **sn \-tp key.publickey**  
  
 下面的代码示例访问私有类型强名称组件。  
  
```  
// friend_assemblies_6.cpp  
// compile by using: /clr /link /keyfile:friend_assemblies.snk  
#using "friend_assemblies_5.dll" as_friend  
  
int main() {  
   Class1 ^ a = gcnew Class1;  
   a->Test_Public();  
}  
```  
  
 **Output**  
  
 `Class1::Test_Public`  
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)