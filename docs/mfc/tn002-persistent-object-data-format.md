---
title: TN002： 持久性对象数据格式 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ca145ff871e1c5ccff27bdebe473c6cb6f39073a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385412"
---
# <a name="tn002-persistent-object-data-format"></a>TN002：持久性对象数据格式
本说明介绍支持持久性 c + + 对象和对象数据的格式时存储在文件中的 MFC 例程。 这仅适用于具有类[DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)宏。  
  
## <a name="the-problem"></a>问题  
 持久性数据的 MFC 实现在单个连续部件的文件中存储为多个对象的数据。 对象的`Serialize`方法将对象的数据转换成精简的二进制格式。  
  
 实现可保证所有数据都保存在相同的格式中使用[CArchive 类](../mfc/reference/carchive-class.md)。 它使用`CArchive`用作一个转换器的对象。 此对象仍然从它创建直到你调用的时存在[CArchive::Close](../mfc/reference/carchive-class.md#close)。 调用此方法可以由程序员显式或隐式通过析构函数在程序退出包含的作用域时`CArchive`。  
  
 本说明介绍的实现`CArchive`成员[CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject)和[CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject)。 你将找到 Arcobj.cpp 和的主要实现中的这些函数的代码`CArchive`Arccore.cpp 中。 用户代码不调用`ReadObject`和`WriteObject`直接。 相反，这些对象由特定于类的插入和提取运算符的类型安全的自动生成`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`宏。 下面的代码演示如何`WriteObject`和`ReadObject`隐式调用：  
  
```  
class CMyObject : public CObject  
{  
    DECLARE_SERIAL(CMyObject) 
};  
 
IMPLEMENT_SERIAL(CMyObj, CObject, 1)  
 
// example usage (ar is a CArchive&)  
CMyObject* pObj;  
CArchive& ar;  
ar <<pObj;        // calls ar.WriteObject(pObj)  
ar>> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))  
```  
  
## <a name="saving-objects-to-the-store-carchivewriteobject"></a>将对象保存到应用商店 (CArchive::WriteObject)  
 该方法`CArchive::WriteObject`写入用于重新构造的对象的标头数据。 此数据由两部分组成： 对象和对象的状态的类型。 此方法也是负责维护写出，该对象的标识，以便保存单个副本，无论包含几个指向该对象 （包括循环指针）。  
  
 保存 （插入），并还原 （解压缩） 对象依赖于几个"清单常量。" 这些都是以二进制形式存储，并提供到存档中 （请注意"w"前缀指示 16 位数量） 的重要信息的值：  
  
|标记|描述|  
|---------|-----------------|  
|wNullTag|用于 NULL 对象指针 (0)。|  
|wNewClassTag|指示后面的类描述不熟悉此存档上下文 (-1)。|  
|wOldClassTag|指示已在此上下文 (0x8000) 中出现所读取的对象类。|  
  
 存档时存储对象，会保留[CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) ( `m_pStoreMap`) 即从存储的对象到 32 位持久标识符 (PID) 的映射。 PID 被分配给每个唯一的对象和存档的上下文中保存的每个唯一的类名称。 按顺序从 1 开始分发这些 Pid。 这些 Pid 存档的作用域之外没有任何意义，特别是，是无法与记录号或其他标识项相混淆。  
  
 在`CArchive`类，Pid 是 32 位，但它们写出为 16 位除非它们是大于 0x7FFE。 大型 Pid 编写为 0x7FFF 跟 32 位 PID。 这将保持与早期版本中创建的项目的兼容性。  
  
 当发出请求以将对象写入存档保存 （通常通过使用全局插入运算符） 时，对于空进行检查[CObject](../mfc/reference/cobject-class.md)指针。 如果指针为 NULL，`wNullTag`插入存档流。  
  
 如果指针不为 NULL，并且可以序列化 (此类是`DECLARE_SERIAL`类)，代码将检查`m_pStoreMap`以查看是否已保存的对象。 如果具有，代码将插入到存档流与该对象相关联的 32 位 PID。  
  
 如果对象没有保存过，有两种可能需要考虑： 对象和对象的确切类型 （即，类） 不熟悉此存档上下文中，或的对象是已检测到的确切类型。 若要确定是否已出现类型，代码查询`m_pStoreMap`为[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)匹配的对象`CRuntimeClass`与正在保存对象关联的对象。 如果没有匹配项，`WriteObject`插入的标记的按位`OR`的`wOldClassTag`和此索引。 如果`CRuntimeClass`不熟悉此存档上下文中，`WriteObject`将新的 PID 分配给该类并将其存档，前面插入`wNewClassTag`值。  
  
 此类的描述符会插入到存档使用`CRuntimeClass::Store`方法。 `CRuntimeClass::Store` 将类 （见下文） 的架构数字和类的 ASCII 文本名称。 请注意使用 ASCII 文本名称并不保证唯一性的存档跨应用程序。 因此，你应标记数据文件以防止损坏。 以下类信息插入，存档将对象插入`m_pStoreMap`，然后调用`Serialize`方法插入类特定的数据。 将对象插入`m_pStoreMap`之前调用`Serialize`防止该对象的多个副本保存到存储区。  
  
 当返回到初始调用方 （通常根对象的网络），必须调用[CArchive::Close](../mfc/reference/carchive-class.md#close)。 如果你打算执行其他[CFile](../mfc/reference/cfile-class.md)操作，必须调用`CArchive`方法[刷新](../mfc/reference/carchive-class.md#flush)为了防止损坏的存档。  
  
> [!NOTE]
>  此实现未施加每个存档上下文 0x3FFFFFFE 索引的硬的限制。 此数字表示最大数量的唯一对象和类可以保存在单独的存档，但单个磁盘文件可以具有无限的数量的存档上下文。  
  
## <a name="loading-objects-from-the-store-carchivereadobject"></a>从存储区 (CArchive::ReadObject) 加载对象  
 加载 （解压） 对象使用`CArchive::ReadObject`方法和截然相反， `WriteObject`。 与`WriteObject`，`ReadObject`不直接由用户代码; 调用用户代码应调用调用使用类型安全提取运算符`ReadObject`处理预期`CRuntimeClass`。 这将确保提取操作的类型完整性。  
  
 由于`WriteObject`实现分配不断增加的 Pid，从 1 开始 （0 预定义为 NULL 对象），`ReadObject`实现可以使用数组来维护存档上下文的状态。 当 PID 从存储读取，如果 PID 大于当前的上限的`m_pLoadArray`，`ReadObject`知道，新对象 （或类描述） 如下所示。  
  
## <a name="schema-numbers"></a>架构数字  
 架构数字，分配给类时`IMPLEMENT_SERIAL`类的方法中发生，是类实现的"版本"。 架构引用类的实现，不适用于的次数给定的对象已持久 （通常称为对象版本）。  
  
 如果你想要维护的同一个类的多个不同的实现，随着时间的推移，递增该架构，如修改对象的`Serialize`方法实现将可编写可以加载使用较旧版本的存储的对象的代码实现。  
  
 `CArchive::ReadObject`方法会引发[CArchiveException](../mfc/reference/carchiveexception-class.md)时遇到持久的内存中的类描述架构数量不同的存储区的架构数字。 它并不容易从此异常中恢复。  
  
 你可以使用`VERSIONABLE_SCHEMA`结合 (按位`OR`) 你要保留引发此异常的架构版本。 通过使用`VERSIONABLE_SCHEMA`，你的代码可以采取相应的操作其`Serialize`通过检查返回值从函数[CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema)。  
  
## <a name="calling-serialize-directly"></a>调用直接序列化  
 在许多情况下的常规对象存档方案的开销`WriteObject`和`ReadObject`不需要。 这是常见的情况下序列化数据插入[CDocument](../mfc/reference/cdocument-class.md)。 在这种情况下，`Serialize`方法`CDocument`提取或插入运算符使用不直接调用。 文档的内容可能反过来使用更多常规对象存档方案。  
  
 调用`Serialize`直接具有以下优点和缺点：  
  
-   任何额外字节被不添加到存档之前或之后的对象序列化。 这不仅可以使已保存的数据在较小，但让你能够实现`Serialize`例程可以处理任何文件格式。  
  
-   优化 MFC 因此`WriteObject`和`ReadObject`实现和相关的集合将不会链接到你的应用程序除非因其他目的需要更多常规对象存档方案。  
  
-   你的代码没有从旧架构数字中恢复。 这就使文档序列化代码负责编码架构数字、 文件格式的版本号，或任何标识数字你使用的数据文件的开头。  
  
-   通过直接调用序列化任何对象`Serialize`不得使用`CArchive::GetObjectSchema`或必须句柄 (UINT)-1 返回值，该值的版本未知。  
  
 因为`Serialize`称为直接在您的文档，它不通常可能要存档到其父文档引用的文档的子对象。 这些对象必须提供一个指向其容器文档显式或必须使用[CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject)函数映射`CDocument`PID 之前存档这些后指针的指针。  
  
 如前文所述，应编码版本和类信息自己在调用时`Serialize`直接，使你能够同时，仍保持使用较旧的文件的向后兼容性更高版本更改的格式。 `CArchive::SerializeClass`函数可以直接将对象序列化为之前或在调用基类之前显式调用。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

