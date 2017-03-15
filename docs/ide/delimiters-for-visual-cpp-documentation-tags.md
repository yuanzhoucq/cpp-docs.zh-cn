---
title: "Visual C++ 文档标记的分隔符 | Microsoft Docs"
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
  - "XML 文档, 分隔符"
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual C++ 文档标记的分隔符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用文档标记要求分隔符，以指示编译器文档注释位置开始和结束。  
  
 XML 文档标记可以与以下几种分隔符一起使用：  
  
 `///`  
 这是在文档的示例显示和 Visual C\+\+ 项目模板使用的窗体。  
  
 `/** */`  
 这些是多行分隔符。  
  
 有一些格式设置规则，在使用 `/** */` \*\/分隔符时：  
  
-   对于包含 `/**`分隔符的行，因此，如果行的其余部分是空白，行没有为注释处理。  如果第一个字符是空格，该空格字符被忽略，并且行的其余进程。  否则，将 `/**` 分隔符后的整行文本处理为注释的一部分。  
  
-   对包含 `*/`分隔符的行，因此，如果只有空白到 `*/` 分隔符，行被忽略。  否则，将到 `*/` 分隔符为止的那行文本处理为注释的一部分，同时必须遵循以下描述的模式匹配规则。  
  
-   对于行，在从 `/**` 分隔符后启动的类似，编译器将包括选项空白和星号的每一行开始处查找一个常见模式 \(`*`\)，后跟更选项的空白。  如果编译器发现一组通用字符在每行开始，它在 `/**` 分隔符之后将忽略所有行该模式，并且可以包含 `*/` 分隔符的行。  
  
 示例：  
  
-   以下注释中将被处理的唯一部分是以 `<summary>` 开头的行。  下面两个标记格式将产生相同的注释：  
  
    ```  
    /**  
    <summary>text</summary>   
    */  
    /** <summary>text</summary> */  
    ```  
  
-   编译器将架构“\*”在第二个和第三行的开头忽略。  
  
    ```  
    /**  
     * <summary>  
     *  text </summary>*/  
    ```  
  
-   因为没有在第二行，的星号编译器没有找到此注释的模式。  因此，作为注释的一部分，在第二个和第三行的所有文本，直到 `*/`，将处理。  
  
    ```  
    /**  
     * <summary>  
       text </summary>*/  
    ```  
  
-   编译器由于以下两个原因不针对此注释的模式。  首先，不以空格的一致的数字开头在星号之前的行。  其次，第五行是以 Tab 开头的，它并不等效于空格。  因此，作为注释的一部分，从第二行的所有文本直到 `*/` 将处理。  
  
    ```  
    /**  
      * <summary>  
      * text   
     *  text2  
       *  </summary>  
    */  
    ```  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)