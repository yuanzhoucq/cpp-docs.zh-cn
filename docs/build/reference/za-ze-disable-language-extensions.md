---
title: "/Za、/Ze（禁用语言扩展） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions"
  - "/za"
  - "/ze"
  - "VC.Project.VCCLCompilerTool.DisableLanguageExtensions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Za 编译器选项 [C++]"
  - "/Ze 编译器选项 [C++]"
  - "“禁用语言扩展”编译器选项"
  - "启用语言扩展"
  - "语言扩展"
  - "语言扩展, 在编译器中禁用"
  - "Za 编译器选项 [C++]"
  - "-Za 编译器选项 [C++]"
  - "Ze 编译器选项 [C++]"
  - "-Ze 编译器选项 [C++]"
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Za、/Ze（禁用语言扩展）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/Za** 编译器选项为与 ANSI C 或 ANSI C\+\+ 不兼容的语言构造发出错误。  默认的 **\/Ze** 编译器选项启用 Microsoft 扩展。  
  
## 语法  
  
```  
/Za  
/Ze  
```  
  
## 备注  
  
> [!NOTE]
>  **\/Ze** 选项已弃用。  有关详细信息，请参阅[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-cn/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 编译器提供许多在 ANSI C 或 ANSI C\+\+ 标准中指定的那些功能以外的功能。  这些功能统称为 C 和 C\+\+ 的 Microsoft 扩展。  这些扩展在指定 **\/Ze** 选项时可用，而在指定 **\/Za** 选项时不可用。  有关更多信息，请参见[Microsoft C 和 C\+\+ 扩展](../../build/reference/microsoft-extensions-to-c-and-cpp.md)。  
  
 如果打算将程序移植到其他环境，请禁用语言扩展。  编译器将扩展关键字视为简单标识符，禁用其他 Microsoft 扩展，并且自动定义 C 程序的 `__STDC__` 预定义宏。  
  
 与 **\/Za** 一起使用的其他编译器选项可能会影响编译器确保 ANSI 一致性的方式。  例如，**\/Za** 和 [\/fp（指定浮点行为）](../../build/reference/fp-specify-floating-point-behavior.md) 一起使用可能导致意外的行为。  
  
 有关用 **\/Za** 获得标准行为的方式，请参见 [\/Zc](../../build/reference/zc-conformance.md) 编译器选项。  
  
 有关 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 一致性问题的更多信息，请参见 [Visual C\+\+ 中的兼容性和合规性问题](../../misc/compatibility-and-compliance-issues-in-visual-cpp.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“语言”**属性页。  
  
4.  修改**“禁用语言扩展”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)