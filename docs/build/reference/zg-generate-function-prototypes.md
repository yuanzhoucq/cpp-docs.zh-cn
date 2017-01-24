---
title: "/Zg（生成函数原型） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/zg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zg 编译器选项 [C++]"
  - "函数原型, “生成函数原型”编译器选项"
  - "“生成函数原型”编译器选项"
  - "Zg 编译器选项 [C++]"
  - "-Zg 编译器选项 [C++]"
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zg（生成函数原型）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已删除。 为源文件中定义的每个函数创建函数原型，但不编译源文件。  
  
## 语法  
  
```  
/Zg  
```  
  
## 备注  
 此编译器选项不再可用。 已在 Visual C\+\+ 2015 中删除。 此页专为 Visual C\+\+ 较早版本的用户保留。  
  
 函数原型包括函数返回类型和参数类型列表。 参数类型列表是根据函数的形参类型创建的。 将忽略源文件中已存在的任何函数原型。  
  
 原型列表将写入标准输出。 此列表可能有助于验证函数的实参和形参是否兼容。 可通过将标准输出重定向到文件以保存此列表。 然后，可使用 **\#include** 将函数原型列表包括为源文件的一部分。 此操作将引发编译器执行参数类型检查。  
  
 如果使用 **\/Zg** 选项，并且你的程序包含具有结构、枚举或联合类型（或指向这些类型的指针）的形参，则每个结构、枚举或联合类型的声明必须带有标记（名称）。 在以下示例中，标记名为 `MyStruct`。  
  
```  
// Zg_compiler_option.c  
// compile with: /Zg  
typedef struct MyStruct { int i; } T2;  
void f2(T2 * t) {}  
```  
  
 **\/Zg** 已弃用。 Visual C\+\+ 编译器计划移除对较早的 C 样式代码的支持。 有关详细信息，请参阅 [Visual C\+\+ 2005 中弃用的编译器选项](http://msdn.microsoft.com/zh-cn/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”对话框。 有关详细信息，请参阅 [如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  点击“命令行”属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)