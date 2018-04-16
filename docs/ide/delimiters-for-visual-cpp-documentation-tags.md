---
title: "Visual c + + 文档标记分隔符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 134605f86ef8019d34f5246fd75abbbf94d40fbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Visual C++ 文档标记的分隔符
文档标记的使用要求信息指示给编译器的文档注释的开始和结束位置的分隔符。  
  
 可以使用以下采用 XML 文档标记的分隔符：  
  
 `///`  
 这是文档示例中所示，使用 Visual c + + 项目模板的窗体。  
  
 `/** */`  
 这些都是多行分隔符。  
  
 有一些格式设置规则时使用`/** */`分隔符：  
  
-   有关包含的行`/**`分隔符，如果该行的其余部分是空格，行未处理的注释。 如果第一个字符是空格，忽略空白字符和处理的行的剩余部分。 否则，将 `/**` 分隔符后面的行的所有文本作为注释的一部分进行处理。  
  
-   有关包含的行`*/`分隔符，如果最多只有空格`*/`分隔符，该行将被忽略。 否则，`*/` 分隔符前面的行的文本被处理为注释的一部分，并且需符合后面的项目符号所描述的模式匹配规则。  
  
-   为开头的一个后的几行`/**`分隔符，编译器会寻找一种常见模式包含可选空格和星号每行的开头 (`*`) 后, 跟多个可选的空白区域。 如果编译器找到每个行的开头的一组通用的字符，它将忽略该模式中的所有行`/**`分隔符，达且可能包括一行，其中包含`*/`分隔符。  
  
 示例如下：  
  
-   以下注释中将被处理的唯一部分是以 `<summary>` 开头的行。 以下两个标记格式将产生相同的注释：  
  
    ```  
    /**  
    <summary>text</summary>   
    */  
    /** <summary>text</summary> */  
    ```  
  
-   编译器在应用的模式"*"若要忽略在第二个和第三个行的开头。  
  
    ```  
    /**  
     * <summary>  
     *  text </summary>*/  
    ```  
  
-   因为在第二行没有星号，编译器在此注释中查找任何模式。 因此，所有文本的第二个和第三个行，直到`*/`，将作为注释的一部分处理。  
  
    ```  
    /**  
     * <summary>  
       text </summary>*/  
    ```  
  
-   编译器找到任何模式此注释中有两个原因。 首先，没有行开头一致前星号的空格数。 其次，第 5 行以制表符开头，这与空格不匹配。 因此，直到第二个行中的所有文本`*/`将作为注释的一部分处理。  
  
    ```  
    /**  
      * <summary>  
      * text   
     *  text2  
       *  </summary>  
    */  
    ```  
  
## <a name="see-also"></a>请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)