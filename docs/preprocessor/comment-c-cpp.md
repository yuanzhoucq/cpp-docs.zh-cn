---
title: "注释 (C/C++) | Microsoft Docs"
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
  - "vc-pragma.comment"
  - "comment_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "批注 [C++]"
  - "注释杂注"
  - "注释 [C++], 编译的文件"
  - "杂注, 注释"
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 注释 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将注释记录置于对象文件或可执行文件中。  
  
## 语法  
  
```  
  
#pragma comment( comment-type [,"commentstring"] )  
```  
  
## 备注  
 *comment\-type* 是一个预定义的标识符（如下所述），它指定了注释记录的类型。  可选 `commentstring` 是一个字符串，它提供了某些注释类型的附加信息。  由于 `commentstring` 是一个字符串，因此它遵循有关转义字符、嵌入的引号 \(**"**\) 和串联的字符串的所有规则。  
  
 **compiler**  
 将编译器的名称和版本号置于对象文件中。  此注释记录将被链接器忽略。  如果为此记录类型提供 `commentstring` 参数，则编译器会生成警告。  
  
 **exestr**  
 将 `commentstring` 置于对象文件中。  在链接时，会将该字符串置于可执行文件内。  加载可执行文件时，不会将字符串加载到内存中；但是，可以使用在文件中查找可打印字符串的程序来找到它。  此注释记录类型的一个用途是将版本号或类似信息嵌入可执行文件中。  
  
 在将来版本中，将弃用和移除 `exestr`；链接器不会处理注释记录。  
  
 **lib**  
 将库搜索记录置于对象文件中。  此注释类型必须带有包含您希望链接器搜索的库的名称（和可能的路径）的 `commentstring` 参数。  库名称遵循对象文件中的默认库搜索记录；链接器会搜索此库，这就像在命令行上对其命名一样，前提是未使用 [\/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md) 指定库。  可以将多个库搜索记录置于同一个源文件中；各个记录将以其在源文件中显示的顺序出现在对象文件中。  
  
 如果默认库和添加的库的顺序很重要，则使用 [\/Zl](../build/reference/zl-omit-default-library-name.md) 开关进行编译会阻止将默认库名称置于对象模块中。  然后，可使用另一个注释杂注在添加的库的后面插入默认库的名称。  与这些杂注一起列出的库将以其在源代码中的发现顺序出现在对象模块中。  
  
 **linker**  
 将[链接器选项](../build/reference/linker-options.md)置于对象文件中。  可以使用注释类型来指定链接器选项，而不是将其传递到命令行或在开发环境中指定它。  例如，可以指定 \/include 选项来强制包含符号：  
  
```  
#pragma comment(linker, "/include:__mySymbol")  
```  
  
 仅以下 \(*comment\-type*\) 链接器选项可传递给链接器标识符：  
  
-   [\/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)  
  
-   [\/EXPORT](../build/reference/export-exports-a-function.md)  
  
-   [\/INCLUDE](../build/reference/include-force-symbol-references.md)  
  
-   [\/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)  
  
-   [\/MERGE](../build/reference/merge-combine-sections.md)  
  
-   [\/SECTION](../build/reference/section-specify-section-attributes.md)  
  
 **User — 用户**  
 将一般注释置于对象文件中。  `commentstring` 参数包含注释文本。  此注释记录将被链接器忽略。  
  
 以下杂注会促使链接器在链接时搜索 EMAPI.LIB 库。  链接器首先在当前工作目录中搜索，然后在 LIB 环境变量指定的路径中搜索。  
  
```  
#pragma comment( lib, "emapi" )  
```  
  
 以下杂注会促使编译器将其名称和版本号置于对象文件中：  
  
```  
#pragma comment( compiler )  
```  
  
> [!NOTE]
>  对于接受 `commentstring` 参数的注释，可以在使用字符串的任何位置使用宏，前提是该宏扩展到字符串。  您还可以字符串与扩展到字符串的宏的任意组合串联在一起。  例如，以下语句是可接受的：  
  
```  
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )   
```  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)