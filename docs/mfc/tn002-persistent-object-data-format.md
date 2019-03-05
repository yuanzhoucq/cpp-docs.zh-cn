---
title: TN002:持久性对象数据格式
ms.date: 11/04/2016
f1_keywords:
- vc.data
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: 6d64799dc17b4b3ddc5c455333b10282e4748b09
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282001"
---
# <a name="tn002-persistent-object-data-format"></a>TN002:持久性对象数据格式

此注释描述 MFC 例程，支持 c + + 的持久性对象和对象数据的格式存储在文件中时。 这仅适用于具有类[DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial)并[IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)宏。

## <a name="the-problem"></a>问题

持久性数据的 MFC 实现将为多个对象的数据存储在单个连续文件的一部分。 对象的`Serialize`方法将精简的二进制格式转换为对象的数据。

实现可保证所有数据都保存在相同的格式中使用[CArchive 类](../mfc/reference/carchive-class.md)。 它使用`CArchive`为翻译对象。 此对象从其创建在您调用之前的时间会一直保持[CArchive::Close](../mfc/reference/carchive-class.md#close)。 调用此方法可以由程序员显式或隐式的析构函数在程序退出包含作用域时`CArchive`。

本说明介绍的实现`CArchive`成员[CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject)并[CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject)。 你将找到 Arcobj.cpp，主要的和实施指南中的这些函数的代码`CArchive`Arccore.cpp 中。 用户代码不会调用`ReadObject`和`WriteObject`直接。 相反，这些对象使用特定于类的插入和提取运算符的类型安全的自动生成的 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏。 下面的代码演示如何`WriteObject`和`ReadObject`隐式调用：

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

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>将对象保存到存储区 (CArchive::WriteObject)

该方法`CArchive::WriteObject`写入用于重新构造对象的标头数据。 此数据由两部分组成： 对象和对象的状态的类型。 此方法也是负责维护正在写出，该对象的标识，以便保存一个副本，无论包含几个指向该对象 （包括循环的指针） 的指针。

保存 （插入） 和还原 （解压缩） 对象依赖于多个"清单常量。" 这些都是二进制文件中存储并提供到存档 （请注意"w"前缀表示 16 位数量） 的重要信息的值：

|标记|描述|
|---------|-----------------|
|wNullTag|用于 NULL 对象的指针 (0)。|
|wNewClassTag|指示类描述不熟悉此存档上下文 (-1)。|
|wOldClassTag|指示所读取的对象类出现在此上下文中 (0x8000)。|

当存储对象，存档将保持[CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) ( *m_pStoreMap*) 这是从一个存储对象到 32 位的永久标识符 (PID) 的映射。 PID 分配给每个唯一对象和保存在存档的上下文中的每个唯一的类名称。 按顺序从 1 开始分发这些 Pid。 这些 Pid 存档的讨论范围内没有任何意义，特别是，将不会与记录号或其他标识项混淆。

在`CArchive`，Pid 为 32 位，但它们写出为 16 位除非它们是大于 0x7FFE。 大型 Pid 编写为 0x7FFF 跟 32 位 PID。 这将保持与早期版本中创建的项目的兼容性。

当发出请求以将对象保存到存档 （通常通过使用全局插入运算符） 时，将进行检查的 null [CObject](../mfc/reference/cobject-class.md)指针。 如果指针为 NULL， *wNullTag*插入到存档流。

如果指针不为 NULL，且可序列化 (此类是`DECLARE_SERIAL`类)，代码将检查*m_pStoreMap*若要查看该对象是否已保存。 如果是，代码将插入到存档流与该对象关联的 32 位 PID。

如果该对象尚未保存之前，有两种可能需要考虑： 对象和对象的确切类型 （即类） 不熟悉此存档上下文中，或该对象是已看到的确切类型。 若要确定是否知道类型，代码查询*m_pStoreMap*有关[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)匹配的对象`CRuntimeClass`与保存的对象相关联的对象。 如果没有匹配项，`WriteObject`插入标记的按位`OR`的*wOldClassTag*和此索引。 如果`CRuntimeClass`存档此上下文中，新增`WriteObject`到该类分配新的 PID，并将其插入到存档，前面有*wNewClassTag*值。

此类的描述符会插入到存档使用`CRuntimeClass::Store`方法。 `CRuntimeClass::Store` 将插入架构数类 （见下文） 和类的 ASCII 文本名称。 请注意使用 ASCII 文本名称跨应用程序不保证存档的唯一性。 因此，应标记数据文件以防止损坏。 以下类信息插入，存档将对象插入*m_pStoreMap* ，然后调用`Serialize`方法插入特定于类的数据。 将放置到的对象*m_pStoreMap*然后才能调用`Serialize`防止该对象的多个副本保存到存储区。

如果返回到初始调用方 （通常根对象的网络），必须调用[CArchive::Close](../mfc/reference/carchive-class.md#close)。 如果你打算执行其他[CFile](../mfc/reference/cfile-class.md)操作，必须调用`CArchive`方法[刷新](../mfc/reference/carchive-class.md#flush)为了防止损坏的存档。

> [!NOTE]
>  此实现未施加硬限制为每个存档上下文 0x3FFFFFFE 索引。 此数字表示的最大数的唯一对象和类，可以保存在单独的存档，但单个磁盘文件可以有无限的数量的存档上下文。

## <a name="loading-objects-from-the-store-carchivereadobject"></a>从存储区 (CArchive::ReadObject) 加载对象

正在加载 （提取） 对象使用`CArchive::ReadObject`方法和截然相反， `WriteObject`。 如同`WriteObject`，`ReadObject`不直接由用户代码; 调用用户代码应调用调用类型安全提取运算符`ReadObject`使用所需`CRuntimeClass`。 这确保了类型的提取操作的完整性。

由于`WriteObject`实现分配不断增加的 Pid，从 1 开始 （0 预定义的为 NULL 对象），`ReadObject`实现可以使用数组来维护存档上下文的状态。 PID 读取时从存储区中，如果值大于当前的上限的 PID *m_pLoadArray*，`ReadObject`知道，新的对象 （或类说明） 如下所示。

## <a name="schema-numbers"></a>架构数字

架构数字，分配给类时`IMPLEMENT_SERIAL`类的方法发生，是类实现的"版本"。 架构是指类的实现，不适用于的次数的给定的对象进行持久 （通常称为对象版本）。

如果你想要维护的同一个类的多个不同实现，随着时间的推移，递增该架构，如修改对象的`Serialize`方法实现将使您能够编写可以加载使用较旧版本的存储对象的代码实现。

`CArchive::ReadObject`方法将引发[CArchiveException](../mfc/reference/carchiveexception-class.md)时遇到持久存储在内存中的类描述的架构数字与不同的架构数字。 它并不容易从此异常中恢复。

可以使用`VERSIONABLE_SCHEMA`结合 (按位**或**) 你要保留引发此异常的架构版本。 通过使用`VERSIONABLE_SCHEMA`，你的代码可以采取相应的操作其`Serialize`通过检查的返回值的函数[CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema)。

## <a name="calling-serialize-directly"></a>直接调用序列化

在许多情况下的常规对象存档方案的开销`WriteObject`和`ReadObject`不是必需的。 这是常见的情况下序列化到数据[CDocument](../mfc/reference/cdocument-class.md)。 在这种情况下，`Serialize`方法的`CDocument`直接调用，不能与提取或插入运算符。 文档的内容可能会反过来使用更多常规对象存档方案。

调用`Serialize`直接具有以下优点和缺点：

- 到之前的存档将对象序列之后，或不添加任何额外的字节。 这不仅可以使已保存的数据在较小，但允许您实现`Serialize`例程可以处理任何文件格式。

- MFC 进行优化，因此`WriteObject`和`ReadObject`实现和相关的集合不会链接到你的应用程序除非所需的其他用途的更多常规对象存档方案。

- 你的代码没有从旧架构数字中恢复。 这使您的文档序列化代码负责编码架构数字、 文件格式的版本号，或任何标识数字，数据文件的开头使用。

- 通过直接调用序列化的任何对象`Serialize`一定不能使用`CArchive::GetObjectSchema`，或必须句柄返回值为 (UINT)-1 指示的版本未知。

因为`Serialize`称为直接在您的文档，它不是通常可以为要存档到其父文档引用的文档的子对象。 这些对象必须提供一个指向其容器文档显式或必须使用[CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject)用于将映射函数`CDocument`PID 之前存档这些反向指针的指针。

如前文所述，应该对版本进行编码和类信息自行调用时`Serialize`直接，使您能够将格式更改同时仍保持向后兼容的较旧的文件的更高版本。 `CArchive::SerializeClass`之前直接序列化对象或调用基类之前可以显式调用函数。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
