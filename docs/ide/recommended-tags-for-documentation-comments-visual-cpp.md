---
title: "建议用于文档注释的标记 (Visual C++) | Microsoft Docs"
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
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建议用于文档注释的标记 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 编译器将处理在代码的文档注释并创建每次编译的 .xdc 文件，并且，用于将处理 .xdc 文件添加到 .xml 文件。  处理 .xml 文件创建文档需要在站点中实现的详细信息。  
  
 标记在结构化过程如类型和类型成员。  
  
 标记必须紧邻类型或成员。  
  
> [!NOTE]
>  文档注释不能应用于命名空间或在属性和事件的不协调定义；文档注释在类的声明必须。  
  
 编译器将处理任何为有效 XML 的标记。  下面的标记提供在用户文档的常用功能：  
  
||||  
|-|-|-|  
|[\<c\>](../ide/c-visual-cpp.md)|[\<code\>](../ide/code-visual-cpp.md)|[\<example\>](../ide/example-visual-cpp.md)|  
|[\<exception\>](../ide/exception-visual-cpp.md)1|[\<include\>](../ide/include-visual-cpp.md)1|[\<list\>](../ide/list-visual-cpp.md)|  
|[\<para\>](../ide/para-visual-cpp.md)|[\<param\>](../ide/param-visual-cpp.md)1|[\<paramref\>](../ide/paramref-visual-cpp.md)1|  
|[\<permission\>](../ide/permission-visual-cpp.md)1|[\<remarks\>](../ide/remarks-visual-cpp.md)|[\<returns\>](../ide/returns-visual-cpp.md)|  
|[\<see\>](../ide/see-visual-cpp.md)1|[\<seealso\>](../ide/seealso-visual-cpp.md)1|[\<summary\>](../ide/summary-visual-cpp.md)|  
|[\<value\>](../ide/value-visual-cpp.md)|||  
  
 1.  编译器将验证语法。  
  
 在当前版本中，Visual C\+\+ 编译器不支持 `<paramref>`，由其他 Visual Studio 编译器支持的标记。  Visual C\+\+ 支持在将来的版本 `<paramref>`。  
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)