---
title: "创建 CArchive 对象的两种方法 | Microsoft Docs"
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
  - "CArchive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive 类, 关闭 CArchive 对象"
  - "CArchive 类, 构造函数"
  - "CArchive 对象"
  - "CArchive 对象, 关闭"
  - "数据存储 [C++], CArchive 类"
  - "I/O [MFC], 创建 CArchive 对象"
  - "序列化 [C++], CArchive 类"
  - "存储 [C++], CArchive 类"
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 创建 CArchive 对象的两种方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用下列两种方法创建 `CArchive` 对象：  
  
-   [一 CArchive 对象的隐式创建框架通过](#_core_implicit_creation_of_a_carchive_object_via_the_framework)  
  
-   [CArchive 显式创建的对象](#_core_explicit_creation_of_a_carchive_object)  
  
##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> 一 CArchive 对象的隐式创建框架通过  
 最常见且最简单方法是，使框架代表保存，另存为创建文档的 `CArchive` 对象并打开" File "菜单上的命令。  
  
 这是框架执行，当应用程序的用户发送从"文件"菜单中的另存为指令：  
  
1.  存在 **另存为** 对话框并从用户那里获取文件名。  
  
2.  打开用户指定的文件作为 `CFile` 对象。  
  
3.  创建点到此 `CFile` 的对象的 `CArchive` 对象。  在创建 `CArchive` 对象，框架设置模式“存储”\(编写，序列化\)，与“负载相对”\(读取，反序列化\)。  
  
4.  **CDocument**中派生类调用 `Serialize` 函数定义，将其传递给 `CArchive` 对象的引用。  
  
 文档的 `Serialize` 函数来将数据写入 `CArchive` 对象，按照说明信息。  一旦从 `Serialize` 函数的返回，框架会销毁 `CArchive` 对象和 `CFile` 对象。  
  
 因而，如果您有框架创建文档的 `CArchive` 对象，只需实现进出存档编写和读取的文档的 `Serialize` 函数。  您还必须实现 `CObject`的所有 `Serialize` 派生对象文档的 `Serialize` 函数直接或间接又序列化。  
  
##  <a name="_core_explicit_creation_of_a_carchive_object"></a> CArchive 显式创建的对象  
 除了进行序列化后，当您可能需要 `CArchive` 对象时，一个文档框架外通过，还有其他一些情况下。  例如，您可能希望向\/从剪贴板将数据序列化，由 `CSharedFile` 对象表示。  或者，可能需要使用用户界面保存与框架提供的版本不同的文件。  在这种情况下，您可以创建新 `CArchive`。  使用以下过程，此框架通过的方法相同。  
  
#### 显式创建 CArchive 对象  
  
1.  从 `CFile`或派生自对象的 `CFile` 对象。  
  
2.  如下例所示，传递给构造函数的 `CFile` 对象的 `CArchive`，例如：  
  
     [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/CPP/two-ways-to-create-a-carchive-object_1.cpp)]  
  
     给 `CArchive` 构造函数的第二个参数是用于指定的枚举值是否为或存储存档加载数据将使用方式出入文件。  对象的 `Serialize` 存档函数通过调用对象的 `IsStoring` 函数检查此状态。  
  
 当您完成时存储或方式出入 `CArchive` 中加载数据对象，请关闭它。  虽然 `CArchive` \(和 `CFile`\) 对象将自动关闭 \(\) 存档和文件，最好到显式引用，因为它从错误恢复使更容易。  有关错误处理的更多信息，请参见知识库文章 [异常：捕获异常和删除](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
#### 关闭 CArchive 对象  
  
1.  下面的示例阐释了 `CArchive` 对象的用法。  
  
     [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/CPP/two-ways-to-create-a-carchive-object_2.cpp)]  
  
## 请参阅  
 [序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)