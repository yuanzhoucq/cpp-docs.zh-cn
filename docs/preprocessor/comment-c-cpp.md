---
title: "注释 （C/c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.comment
- comment_CPP
dev_langs:
- C++
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d1062923f50470a2238af21676c4137fac241905
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="comment-cc"></a>注释 (C/C++)
将注释记录置于对象文件或可执行文件中。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma comment( comment-type [,"commentstring"] )  
```  
  
## <a name="remarks"></a>备注  
 *注释类型*指定注释记录的类型的一个，如下所述的预定义标识符。 可选 `commentstring` 是一个字符串，它提供了某些注释类型的附加信息。 因为`commentstring`是字符串，它遵循有关转义字符、 嵌入的引号的字符串的所有规则 (**"**)，和串联。  
  
 **compiler**  
 将编译器的名称和版本号置于对象文件中。 此注释记录将被链接器忽略。 如果为此记录类型提供 `commentstring` 参数，则编译器会生成警告。  
  
 **exestr**  
 将 `commentstring` 置于对象文件中。 在链接时，会将该字符串置于可执行文件内。 加载可执行文件时，不会将字符串加载到内存中；但是，可以使用在文件中查找可打印字符串的程序来找到它。 此注释记录类型的一个用途是将版本号或类似信息嵌入可执行文件中。  
  
 在将来版本中，将弃用和移除 `exestr`；链接器不会处理注释记录。  
  
 **lib**  
 将库搜索记录置于对象文件中。 此注释类型必须带有包含您希望链接器搜索的库的名称（和可能的路径）的 `commentstring` 参数。 库名称遵循对象文件中; 中的默认库搜索记录在链接器搜索此库，就像你必须将其命名为命令行上提供，未指定库[/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md)。 可以将多个库搜索记录置于同一个源文件中；各个记录将以其在源文件中显示的顺序出现在对象文件中。  
  
 如果默认库和添加的库的顺序很重要，编译[/Zl](../build/reference/zl-omit-default-library-name.md)交换机将阻止默认库名称置于对象模块。 然后，可使用另一个注释杂注在添加的库的后面插入默认库的名称。 与这些杂注一起列出的库将以其在源代码中的发现顺序出现在对象模块中。  
  
 **linker**  
 位置[链接器选项](../build/reference/linker-options.md)对象文件中。 可以使用注释类型来指定链接器选项，而不是将其传递到命令行或在开发环境中指定它。 例如，可以指定 /include 选项来强制包含符号：  
  
```  
#pragma comment(linker, "/include:__mySymbol")  
```  
  
 仅以下 (*注释类型*) 提供了链接器选项以将传递给链接器标识符：  
  
-   [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)  
  
-   [/EXPORT](../build/reference/export-exports-a-function.md)  
  
-   [/INCLUDE](../build/reference/include-force-symbol-references.md)  
  
-   [/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)  
  
-   [/MERGE](../build/reference/merge-combine-sections.md)  
  
-   [/SECTION](../build/reference/section-specify-section-attributes.md)  
  
 **user**  
 将一般注释置于对象文件中。 `commentstring` 参数包含注释文本。 此注释记录将被链接器忽略。  
  
 以下杂注会促使链接器在链接时搜索 EMAPI.LIB 库。 链接器首先在当前工作目录中搜索，然后在 LIB 环境变量指定的路径中搜索。  
  
```  
#pragma comment( lib, "emapi" )  
```  
  
 以下杂注会促使编译器将其名称和版本号置于对象文件中：  
  
```  
#pragma comment( compiler )  
```  
  
> [!NOTE]
>  对于接受 `commentstring` 参数的注释，可以在使用字符串的任何位置使用宏，前提是该宏扩展到字符串。 您还可以字符串与扩展到字符串的宏的任意组合串联在一起。 例如，以下语句是可接受的：  
  
```  
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )   
```  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)