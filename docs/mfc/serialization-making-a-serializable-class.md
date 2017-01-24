---
title: "序列化：定义可序列化的类 | Microsoft Docs"
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
  - "类 [C++], 派生"
  - "CObject 类, 派生可序列化类"
  - "构造函数 [C++], 不采用参数进行定义"
  - "DECLARE_SERIAL 宏"
  - "默认构造函数"
  - "默认值 [C++], 构造函数"
  - "IMPLEMENT_SERIAL 宏"
  - "没有默认构造函数"
  - "无参数构造函数"
  - "可序列化类"
  - "序列化 [C++], 可序列化类"
  - "Serialize 方法, 重写"
  - "VERSIONABLE_SCHEMA 宏"
ms.assetid: 59a14d32-1cc8-4275-9829-99639beee27c
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 序列化：定义可序列化的类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

要求五个主要步骤使类可序列化。  他们列举如下，并在下面的章节解释：  
  
1.  [从CObject派生类](#_core_deriving_your_class_from_cobject) \(或者从某个类的派生 `CObject`\).  
  
2.  [序列化重写成员函数](#_core_overriding_the_serialize_member_function)。  
  
3.  在类声明中的[使用 DECLARE\_SERIAL 宏](#_core_using_the_declare_serial_macro)。  
  
4.  [定义没有参数的构造函数](#_core_defining_a_constructor_with_no_arguments)。  
  
5.  类的[使用实现文件中的 IMPLEMENT\_SERIAL 宏](#_core_using_the_implement_serial_macro_in_the_implementation_file)。  
  
 如果浏览 [CArchive](../mfc/reference/carchive-class.md)上和 \<\< 运算符 \>\> 直接调用 `Serialize`，而不是前三个步骤对于序列化是必需的。  
  
##  <a name="_core_deriving_your_class_from_cobject"></a> 从 CObject 派生类  
 基本序列化协议和功能在 `CObject` 类中定义。  通过从 `CObject` 派生类 \(或从 `CObject`派生的类\)，如类中所示 `CPerson`的下列声明，将 `CObject`序列化的协议和功能的访问。  
  
##  <a name="_core_overriding_the_serialize_member_function"></a> 序列化重写成员函数。  
 `Serialize` 成员函数，如 `CObject` 类中定义，则实际序列化需要的数据运行捕获对象的当前状态。  `Serialize` 函数具有使用它读取的 `CArchive` 参数并编写对象数据。  [CArchive](../mfc/reference/carchive-class.md) 对象有成员函数，`IsStoring`，指示 `Serialize` 是否存储 \(写入数据\) 或加载 \(读取数据。  使用 `IsStoring` 结果作为指南，则插入到 `CArchive` 对象的数据。粘贴运算符 \(**\<\<**提取\) 或使用运算符 \(**\>\>**\) 中提取数据。  
  
 考虑从 `CObject` 派生并包含两个新成员变量的类类型，`CString` 和 **WORD**。  以下片段类声明显示新成员变量和声明重写的 `Serialize` 成员函数中：  
  
 [!code-cpp[NVC_MFCSerialization#1](../mfc/codesnippet/CPP/serialization-making-a-serializable-class_1.h)]  
  
#### 序列化重写成员函数。  
  
1.  调用 `Serialize` 的基类版本，确保对象的继承部分的序列化。  
  
2.  插入或提取特定成员变量添加到类。  
  
     插入和运算符提取与存档类读取和写入数据。  下面的代码示例演示如何实现 `Serialize` 类`CPerson`。  
  
     [!code-cpp[NVC_MFCSerialization#2](../mfc/codesnippet/CPP/serialization-making-a-serializable-class_2.cpp)]  
  
 还可以使用 [CArchive::Read](../Topic/CArchive::Read.md) [CArchive::Write](../Topic/CArchive::Write.md) 和成员函数读取和编写大量非类型化数据。  
  
##  <a name="_core_using_the_declare_serial_macro"></a> 使用 DECLARE\_SERIAL 宏  
 `DECLARE_SERIAL` 宏将支持序列化需要的类声明，如下所示：  
  
 [!code-cpp[NVC_MFCSerialization#3](../mfc/codesnippet/CPP/serialization-making-a-serializable-class_3.h)]  
  
##  <a name="_core_defining_a_constructor_with_no_arguments"></a> 定义没有参数的构造函数  
 MFC 需要默认构造函数，则在重新创建对象时，它们将从磁盘加载 \(\)。  反序列化进程将填写要求值的任何成员变量重新创建对象。  
  
 此构造函数。公共声明，受保护或私有。  如果要使其成为受保护或私有，有助于确保，它将会由序列化函数仅使用。  构造函数必须在允许如有必要，删除的状态将对象。  
  
> [!NOTE]
>  如果忘记定义构造函数没有在使用 `DECLARE_SERIAL` 和 `IMPLEMENT_SERIAL` 宏的类的参数，则将获得“没有默认构造函数在使用 `IMPLEMENT_SERIAL` 宏的行可用”编译器警告。  
  
##  <a name="_core_using_the_implement_serial_macro_in_the_implementation_file"></a> 使用实现文件中的 IMPLEMENT\_SERIAL 宏  
 当您从 `CObject`派生一个类时，可以 `IMPLEMENT_SERIAL` 宏来定义所需要的各种功能。  在实现文件 \(.cpp\) 使用此宏为类。  至宏的最后两个参数是类的名称以及其直接基类的名称。  
  
 该宏的第三个参数是一架构数字。  数字架构本质上是类的对象的版本号。  为架构数字使用整数值大于或等于 0。\(不要将此架构数字混淆数据库术语。\)  
  
 MFC 序列化代码检查架构，当数字对象读取到内存时。  如果对象架构数字磁盘上不匹配。类架构的编号在内存中，库将引发 `CArchiveException`，这会阻止程序读取对象不正确的版本。  
  
 如果希望 `Serialize` 成员函数可读取多版本 \(即，用文件写入应用程序的不同版本 \- 可以使用值 **VERSIONABLE\_SCHEMA** 作为参数传给 `IMPLEMENT_SERIAL` 宏。  有关用法信息和示例，请参见 `CArchive`类的 `GetObjectSchema` 成员函数。  
  
 下面的示例演示如何定义从 `IMPLEMENT_SERIAL``CPerson` 中派生`CObject`的类。  
  
 [!code-cpp[NVC_MFCSerialization#4](../mfc/codesnippet/CPP/serialization-making-a-serializable-class_4.cpp)]  
  
 一旦具有了序列化类，您可以将该类序列化的对象，如下所述。文章 [序列化：序列化对象](../mfc/serialization-serializing-an-object.md)  
  
## 请参阅  
 [序列化](../mfc/serialization-in-mfc.md)