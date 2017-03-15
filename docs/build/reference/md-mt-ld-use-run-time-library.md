---
title: "/MD、/MT、/LD（使用运行库） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ld"
  - "/mt"
  - "VC.Project.VCCLWCECompilerTool.RuntimeLibrary"
  - "VC.Project.VCCLCompilerTool.RuntimeLibrary"
  - "/md"
  - "/ml"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LD 编译器选项 [C++]"
  - "/MD 编译器选项 [C++]"
  - "/MDd 编译器选项 [C++]"
  - "/MT 编译器选项 [C++]"
  - "/MTd 编译器选项 [C++]"
  - "_STATIC_CPPLIB 符号"
  - "DLL [C++], 编译器选项"
  - "LD 编译器选项 [C++]"
  - "-LD 编译器选项 [C++]"
  - "LIBC.lib"
  - "LIBCD.lib"
  - "LIBCMT.lib"
  - "LIBCMTD.lib"
  - "MD 编译器选项 [C++]"
  - "-MD 编译器选项 [C++]"
  - "MDd 编译器选项 [C++]"
  - "-MDd 编译器选项 [C++]"
  - "MSVCRT.lib"
  - "MSVCRTD.lib"
  - "MT 编译器选项 [C++]"
  - "-MT 编译器选项 [C++]"
  - "MTd 编译器选项 [C++]"
  - "-MTd 编译器选项 [C++]"
  - "多线程编译器选项"
  - "线程处理 [C++], 多线程编译器选项"
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# /MD、/MT、/LD（使用运行库）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示多线程模块是否为 DLL，并指定运行库的零售版本或调试版本。  
  
## 语法  
  
```  
/MD[d]  
/MT[d]  
/LD[d]  
```  
  
## 备注  
  
|选项|说明|  
|--------|--------|  
|**\/MD**|使此应用程序使用特定于多线程和 DLL 的运行库版本。  定义 `_MT` 和 `_DLL`，并使编译器将库名 MSVCRT.lib 放入 .obj 文件中。<br /><br /> 用此选项编译的应用程序静态链接到 MSVCRT.lib。  此库提供使链接器能够解析外部引用的代码的层。  实际工作代码包含在 MSVCR*versionnumber*.DLL 中，后者必须在运行时对与 MSVCRT.lib 链接的应用程序可用。|  
|**\/MDd**|定义 `_DEBUG`、`_MT` 和 `_DLL`，并使此应用程序使用特定于多线程和 DLL 的调试版本的运行库。  它还会让编译器将库名称 MSVCRTD.lib 放入 .obj 文件中。|  
|**\/MT**|使此应用程序使用运行库的多线程的静态版本。  定义 `_MT`，并使编译器将库名 LIBCMT.lib 放入 .obj 文件中，以便链接器使用 LIBCMT.lib 解析外部符号。|  
|**\/MTd**|定义 `_DEBUG` 和 `_MT`。  此选项还会让编译器将库名称 LIBCMTD.lib 放置到 .obj 文件中，以便链接器将使用 LIBCMTD.lib 来解析外部符号。|  
|**\/LD**|创建一个 DLL。<br /><br /> 将 **\/DLL** 选项传递到链接器。  链接器查找 `DllMain` 函数，但并不需要该函数。  如果没有编写 `DllMain` 函数，则链接器将插入返回 TRUE 的 `DllMain` 函数。<br /><br /> 链接 DLL 启动代码。<br /><br /> 如果未在命令行上指定导出 \(.exp\) 文件，则创建导入库 \(.lib\)。  将导入库链接到调用 DLL 的应用程序。<br /><br /> 将 [\/Fe（命名 EXE 文件）](../../build/reference/fe-name-exe-file.md) 解释为命名 DLL 而不是 .exe 文件。  默认情况下，程序名会变成 *basename*.dll 而不是 *basename*.exe。<br /><br /> 除非显式指定 **\/MD**，否则将暗指 **\/MT**。|  
|**\/LDd**|创建调试 DLL。  定义 `_MT` 和 `_DEBUG`。|  
  
 有关 C 运行库以及使用 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md) 进行编译时要使用哪些库的更多信息，请参见 [CRT 库功能](../../c-runtime-library/crt-library-features.md)。  
  
 传递给链接器的给定调用的所有模块都必须使用相同的运行库编译器选项（**\/MD**、**\/MT**、**\/LD**）进行编译。  
  
 有关如何使用运行库的调试版本的更多信息，请参见[C 运行时库参考](../../c-runtime-library/c-run-time-library-reference.md)。  
  
 知识库文章 Q140584 也讨论如何选择适当的 C 运行库。  
  
 有关 DLL 的更多信息，请参见 [Visual C\+\+ 中的 DLL](../../build/dlls-in-visual-cpp.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“C\/C\+\+”**文件夹。  
  
3.  选择**“代码生成”**属性页。  
  
4.  修改**“运行库”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)