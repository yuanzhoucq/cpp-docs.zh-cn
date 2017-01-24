---
title: "__identifier | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__identifier"
  - "__identifier_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__identifier 关键字 [C++]"
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __identifier
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

启用使用 Visual C\+\+ 关键字用作标识符。  
  
## 所有平台  
 **语法**  
  
```  
  
__identifier(  
Visual_C++_keyword  
)  
  
```  
  
 **备注**  
  
 使用不包含关键字的标识符的 `__identifier` 关键字的用法是允许，但强烈不建议这种样式。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
  
### 要求  
 编译器选项：**\/ZW**  
  
### 示例  
 **示例**  
  
 在下面的示例中，名为 `template` 的类创建并分发 C\# 作为 DLL。  在使用 `template` 类的 Visual C\+\+ 程序，`__identifier` 关键字都会隐藏事实 `template` 是标准 C\+\+ 关键字。  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /ZW  
#using <identifier_template.dll>  
int main() {  
   __identifier(template)^ pTemplate = ref new __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **备注**  
  
 `__identifier` 关键字是有效的。**\/clr** 和 **\/clr:oldSyntax** 编译器选项。  
  
### 要求  
 编译器选项：**\/clr**  
  
### 示例  
 **示例**  
  
 在下面的示例中，名为 `template` 的类创建并分发 C\# 作为 DLL。  在使用 `template` 类的 Visual C\+\+ 程序，`__identifier` 关键字都会隐藏事实 `template` 是标准 C\+\+ 关键字。  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /clr  
#using <identifier_template.dll>  
  
int main() {  
   __identifier(template) ^pTemplate = gcnew __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)   
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)