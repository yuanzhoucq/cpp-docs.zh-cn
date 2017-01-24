---
title: "XML 文档 (Visual C++) | Microsoft Docs"
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
  - "用于 C++ 文档的 /// 分隔符"
  - "注释, C++ 源代码文件"
  - "XML 文档"
  - "XML, 源代码中的文档注释"
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# XML 文档 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 Visual C\+\+ 中，可以将注释添加到将处理到 .xml 文件的源代码。  此文件可以是输入到在代码中创建选件类的文档的处理。  
  
 在 Visual C\+\+ 代码文件，XML 必须直接在方法或类型定义之前位于文档注释。  注释可以使用该在下列方案中的 Intellisense 以前的数据提示：  
  
1.  当代码编译为具有附带的 .winmd 文件的 windows 运行时组件  
  
2.  当源代码在当前时包括项目  
  
3.  在类型声明和实现位于同一标头文件的库中  
  
> [!NOTE]
>  在当前版本中，代码注释中包含模板类型 \(例如，函数的模板或任何未处理采用参数作为模板\)。  添加这样的注释生成未定义的行为。  
  
 有关创建 .xml 文件的详细信息。文档注释，请参见下列主题。  
  
|有关以下内容的信息|请参见|  
|---------------|---------|  
|使用的编译器选项|[\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
|可以使用提供在文档的常用功能的标记|[建议的文档注释标记](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|  
|编译器生成标识代码构造的 ID 字符串|[处理 .xml 文件](../ide/dot-xml-file-processing.md)|  
|如何将文档标记|[Visual C\+\+ 文档标记的分隔符](../ide/delimiters-for-visual-cpp-documentation-tags.md)|  
|生成一个 .xml 文件从一个或多个 .xdc 文件。|[XDCMake 引用](../ide/xdcmake-reference.md)|  
|信息的链接有关 XML，它与 Visual Studio 功能区相关|[在 Visual Studio 中的 XML](../Topic/XML%20Tools%20in%20Visual%20Studio.md)|  
  
 如果需要将 XML 文档文本的特殊字符注释，必须将 XML 实体或 CDATA 节。  
  
## 请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)