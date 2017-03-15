---
title: "使用 CArchive &lt;&lt; 和 &gt;&gt; 运算符 | Microsoft Docs"
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
  - "CArchive 类, 运算符"
  - "CArchive 类, 存储和加载对象"
  - "对象 [C++], 从以前存储的值加载"
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 CArchive &lt;&lt; 和 &gt;&gt; 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CArchive` 提供 \<\< 和 \>\> 运算符写入和读取简单数据类型以及 `CObject`s 到和从文件。  
  
#### 通过存档将对象存储在文件中  
  
1.  下面的示例演示如何通过存档将对象存储到文件中：  
  
     [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_1.cpp)]  
  
#### 从先前存储在文件中的值加载对象  
  
1.  下面的示例演示如何从以前存储在文件中的值加载对象：  
  
     [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_2.cpp)]  
  
 通常，在 `CObject` 派生类的 `Serialize` 函数通过存档存储数据到一个文件和从一个文件加载数据，则必须用**DECLARE\_SERIALIZE** 宏声明。  对 `CArchive` 对象的引用传递给 `Serialize` 函数。  调用 `CArchive` 对象的 `IsLoading` 函数确定 `Serialize` 函数是否从文件或存储数据加载到数据文件。  
  
 序列化 `CObject` 派生类的 `Serialize` 的函数通常具有以下形式：  
  
 [!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_3.cpp)]  
  
 以上代码是一 AppWizard 模板正常提供文档的 `Serialize` 函数创建相同的类 \(从 **CDocument\)**派生的类。  此代码模板帮助您编写代码更易于检查，因为存储的代码和加载的代码总是并行，如下面的示例中：  
  
 [!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_4.cpp)]  
  
 库为 `CArchive` 定义了 **\<\<** 和 **\>\>** 运算符作为第一个操作数和以下数据类型和类类型用作第二个操作对象：  
  
||||  
|-|-|-|  
|`CObject*`|**SIZE 和 CSize**|**float**|  
|**WORD**|`CString`|**POINT** 和 `CPoint`|  
|`DWORD`|**BYTE**|`RECT` 和 `CRect`|  
|**Double**|**LONG**|`CTime` 和 `CTimeSpan`|  
|`Int`|**COleCurrency**|`COleVariant`|  
|`COleDateTime`|`COleDateTimeSpan`||  
  
> [!NOTE]
>  存储和加载的 `CObject`s 和存档需要通过额外的注意事项。  有关详细信息，请参阅 [存储和加载的 CObjects 通过存档](../mfc/storing-and-loading-cobjects-via-an-archive.md)。  
  
 **CArchive \<\<** 和 **\>\>** 运算符总是返回对 `CArchive` 对象的引用，是第一个操作数。  这样您可以让运算符，如下所示：  
  
 [!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_5.cpp)]  
  
## 请参阅  
 [序列化：对象的序列化](../mfc/serialization-serializing-an-object.md)