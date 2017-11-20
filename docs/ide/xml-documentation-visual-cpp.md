---
title: "XML 文档 （Visual c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fb5b9968ad652e5ab6ef4dd29eb3c6ccc6da7493
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="xml-documentation-visual-c"></a>XML 文档 (Visual C++)
Visual c + +，你可以在你将处理到一个.xml 文件的源代码中添加注释。 然后，此文件可以是在你的代码中创建的类的文档的进程的输入。  
  
 在 Visual c + + 代码文件中，必须直接在方法或类型定义之前位于 XML 文档注释。 可以使用注释来填充的 Intellisense 快速信息数据提示在以下方案：  
  
1.  使用随附的.winmd 文件时为 Windows 运行时组件编译代码  
  
2.  当在当前项目中包括的源代码  
  
3.  在库中的类型声明和实现都位于相同的标头文件  
  
> [!NOTE]
>  在当前版本中，代码注释不会处理在模板或含有 （例如，接受作为模板参数的函数） 的一种模板类型的所有内容。 添加此类的注释将导致未定义的行为。  
  
 有关创建带有文档注释的.xml 文件的详细信息，请参阅以下主题。  
  
|有关信息|请参阅|  
|---------------------------|---------|  
|要使用的编译器选项|[/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
|标记可用于提供通常使用文档中的功能|[建议的文档注释标记](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|  
|编译器将产生以标识你的代码中的构造 ID 字符串|[处理的.xml 文件](../ide/dot-xml-file-processing.md)|  
|如何分隔文档标记|[Visual C++ 文档标记的分隔符](../ide/delimiters-for-visual-cpp-documentation-tags.md)|  
|从一个或多个.xdc 文件中生成一个.xml 文件。|[XDCMake 参考](../ide/xdcmake-reference.md)|  
|有关 XML 作为它的信息的链接与 Visual Studio 的功能区域|[Visual Studio 中的 XML](/visualstudio/xml-tools/xml-tools-in-visual-studio)|  
  
 如果你需要在的文档注释的文本中放置 XML 特殊字符，必须使用 XML 实体或 CDATA 节。  
  
## <a name="see-also"></a>另请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)