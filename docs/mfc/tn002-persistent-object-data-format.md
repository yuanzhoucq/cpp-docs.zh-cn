---
title: "TN002：持久性对象数据格式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive 类, 对持久性数据的支持"
  - "持久性 C++ 对象"
  - "持久性对象数据"
  - "TN002"
  - "VERSIONABLE_SCHEMA 宏"
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# TN002：持久性对象数据格式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此注释说明MFC 例程支持持久化 C\+\+对象和存储在文件中对象数据的格式。  本节仅适用于使用 [DECLARE\_SERIAL](../Topic/DECLARE_SERIAL.md) and [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) 宏的类。  
  
## 问题  
 MFC实现在文件的单个连续部分的许多对象为持久化存储数据。  对象的 `Serialize` 方法将对象中的数据转换一种精简二进制格式。  
  
 实现保证通过使用 [CArchive Class](../mfc/reference/carchive-class.md) 所有数据保存在同一格式。  它使用 `CArchive` 对象作为转换器。  该对象从创建它开始一直存在，直到调用 [CArchive::Close](../Topic/CArchive::Close.md)。  可由程序员显式或隐式用析构函数调用该方法，并且程序导出包含 `CArchive`的大小。  
  
 此注释说明 `CArchive` 成员、[CArchive::WriteObject](../Topic/CArchive::WriteObject.md)[CArchive::ReadObject](../Topic/CArchive::ReadObject.md) 的实现。  要查找在 Arcobj.cpp这些函数的代码 和在Arccore.cpp `CArchive` 的主要实现。  用户代码不直接调用 `ReadObject` 和 `WriteObject`。  相反，将自动由 `DECLARE_SERIAL` 和 `IMPLEMENT_SERIAL` 宏生成的类特定类型安全、插入和运算符提取使用这些对象。  下面的代码演示 `WriteObject` 和 `ReadObject` 如何隐式调用：  
  
```  
class CMyObject : public CObject  
{  
    DECLARE_SERIAL(CMyObject)  
};  
  
IMPLEMENT_SERIAL(CMyObj, CObject, 1)  
  
// example usage (ar is a CArchive&)  
CMyObject* pObj;  
CArchive& ar;  
ar << pObj;        // calls ar.WriteObject(pObj)  
ar >> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))  
```  
  
## 保持对象到内存\(CArchive::WriteObject\)  
 该方法 `CArchive::WriteObject` 写入用于重构对象的标题数据。  此数据包括两个部分：对象的类型和对象的状态。  此方法也负责维护被写出对象的同一性，以至于只有一个副本保存，无论指针的对象的标识还负责对该对象 \(包括循环的指针\)。  
  
 保存 \(插入\) 以及依赖对象几个“显式常数”恢复 \(提取\) 。这些以二进制存储和提供重要信息以存档的值 \(请注意“w”前缀指示 16 位数\)：  
  
|Tag|说明|  
|---------|--------|  
|wNullTag|用于空对象指针\(0\)。|  
|wNewClassTag|指示以下的类描述对该存档内容是新的 \(\- 1\)。|  
|wOldClassTag|指示读取对象的类在上下文中显示 \(0x8000\)。|  
  
 当存储对象，则从存储的对象映射到 32 位固定标识符 \(PID\) 的存档维护 [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) \( `m_pStoreMap`\)。  PID 分配给保存在存档中每个唯一对象和每个唯一的类名。  这些 PIDs 是以 1 开始实现顺序。  这些 PIDs 在存档的范围外没有意义，特别是，不记录与数字或其他标识项相混淆。  
  
 在 `CArchive` 类中，PIDs 是32 位，但它们以16位被写出，除非它们大于 0x7FFE。  大的 PIDs 跟随 32 位 PID 以 0x7FFF 写出。  这将保留在的早期版本中创建的项目的向后兼容性。  
  
 当生成请求来保存对象 到存档中\(通常通过使用全局运算符插入\)，对空的 [CObject](../mfc/reference/cobject-class.md) 指针进行检查。  如果指针为空时，`wNullTag` 插入到存档流。  
  
 如果指针不为空，并能序列化 \(类是 `DECLARE_SERIAL` 类\)，代码检查的 `m_pStoreMap` 对象是否已保存。  如果有，代码插入与存档流对象有关的 32 位 PID 。  
  
 如果之前对象尚未保存过，则需要考虑两种可能的例外情况：或对象和准确的类型 \(即类\) 存档到此上下文，对象是新的或对象中显示的是一个精确类型。  若要确定类型是否显示了，代码为 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)对象查询 `m_pStoreMap` `CRuntimeClass` 对象与保存的对象匹配。  如果存在匹配项，`WriteObject` 插入一个 `wOldClassTag` 的宽位 `OR` 标签和该索引。  如果 `CRuntimeClass` 是新的存档到此上下文，`WriteObject` 分配新 PID 到该类并将其插入到存档，排在 `wNewClassTag` 值之前。  
  
 使用 `CRuntimeClass::Store` 方法，此类的描述符然后插入到存档。  `CRuntimeClass::Store` 插入类的架构数 \(如下所示\) 和类的 ASCII 数字文本名称。  请注意ASCII 文本名称的使用不保证在应用程序中 Archive 的唯一性。  因此，应标记数据文件以防止丢失。  在插入类信息之后，存档将对象放入 `m_pStoreMap` 然后调用 `Serialize` 方法插入类特定的数据。  在调用`Serialize` 之前将对象放入 `m_pStoreMap` 以防止对象的多个副本保存到存储区。  
  
 当返回到初始调用方\(通常对象网络的跟\) 时，必须调用 [CArchive::Close](../Topic/CArchive::Close.md)。  如果您计划运行其他 [CFile](../mfc/reference/cfile-class.md)操作，必须调用 `CArchive` 方法 [Flush](../Topic/CArchive::Flush.md) 防止存档损坏。  
  
> [!NOTE]
>  此实现将对每存档上下文产生 0x3FFFFFFE 的强烈限制。  此数字表示可以在一个存档保存单个对象和类的最大项数，但一个唯一磁盘文件可以有无限标记的存档上下文。  
  
## 从存储区 \(CArchive::ReadObject\) 加载对象  
 加载 \(提取\) 对象使用 `CArchive::ReadObject` 方法并且 `WriteObject`的转换。  和 `WriteObject`相同，`ReadObject` 未由用户代码直接调用方法；用户代码应调用 `ReadObject` 及需要的 `CRuntimeClass`运算符提取类型安全。  这确保获取操作的类型完整性。  
  
 因为 `WriteObject` 实现将不断增加 PIDs，从 1 开始 \(0 预定义为空\)，对象 `ReadObject` 实现可以使用数组维护上下文的存档状态。  当 PID 从存储区中读取，如果 PID大于 `m_pLoadArray` 的当前上限，则之后 `ReadObject` 识别为新的对象 \(类或说明\) 。  
  
## 架构数字  
 架构数字，当类的 `IMPLEMENT_SERIAL` 方法遇到时，分配的类为类实现的“版本”。  架构设计类的实现，不到使一个特定的对象不可变的次数 \(通常称为对象版本\)。  
  
 如果您希望维护同一类的多个不同实现，添加架构，在修改对象的 `Serialize` 方法实现将可以编写能加载对象存储使用简化的旧版本的代码。  
  
 当遇到在固定存储中的架构数字不同于内存类描述的架构数字，`CArchive::ReadObject` 方法将抛出 [CArchiveException](../mfc/reference/carchiveexception-class.md) 。  从该异常恢复很难。  
  
 可以使用 `VERSIONABLE_SCHEMA` combined with \(bitwise  `OR` 架构版本防止抛出此异常。  通过使用 `VERSIONABLE_SCHEMA`，代码可以通过从 [CArchive::GetObjectSchema](../Topic/CArchive::GetObjectSchema.md)检查返回值在自己的 `Serialize` 函数中采取适当行为。  
  
## 直接调用序列化  
 在许多情况下 `WriteObject` 和 `ReadObject` 泛对象存档方案的系统开销并不是必需的。  将数据序列化到 [CDocument](../mfc/reference/cdocument-class.md) 是常见的情况。  在这种情况下， 未使用提取或运算符插入,直接调用 `CDocument` 的 `Serialize` 方法。  文档的内容可能会使用更常规的对象存档方案。  
  
 直接调用 `Serialize` 具有以下优点和缺点：  
  
-   在对象序列号前后，不要添加额外的字节数到存档。  这不但使保存的数据更少，但允许实现可以处理任何文件格式的 `Serialize` 例程。  
  
-   MFC 调整，因此 `WriteObject` 和 `ReadObject` 实现和相关集合不会链接到应用程序，除非需要其他用途的更常规的对象存档方案。  
  
-   代码不必从早期架构数字恢复。  这使文档序列化代码负责编码架构数字，格式文件版本号，或者任何标识的数字在数据文件中开始使用。  
  
-   直接调用 `Serialize` 的序列号对象无法使用 `CArchive::GetObjectSchema` 或必须处理未知版本的 \(UINT\)\-1的返回值。  
  
 因为在文档上直接调用 `Serialize` ，对于文档的子对象存档引用到其父文档通常是不可能的。  在这些返回指针存档之前，必须显式给这些对象指针指向它们的文档容器或必须使用 [CArchive::MapObject](../Topic/CArchive::MapObject.md) 函数映射 `CDocument` 指向 PID。  
  
 如前所述，当直接调用 `Serialize` 时，您应编码版本和类信息，使您以后可以更改窗体，同时保持与旧的文件时的向后兼容性。  在直接序列化对象之前或在调用基类之前，`CArchive::SerializeClass` 函数可以显式调用。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)