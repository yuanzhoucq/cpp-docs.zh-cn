---
title: TN002：持久性对象数据格式
ms.date: 11/04/2016
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: 1880d5d43055966dea8ab16dc4f26bd4e4602ec5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447131"
---
# <a name="tn002-persistent-object-data-format"></a>TN002：持久性对象数据格式

此注释描述了在文件中存储对象C++数据时支持持久性对象和对象数据格式的 MFC 例程。 这仅适用于具有[DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)宏的类。

## <a name="the-problem"></a>问题

持久性数据的 MFC 实现将多个对象的数据存储在文件的单个连续部分。 对象的 `Serialize` 方法将对象的数据转换为精简二进制格式。

实现使用[CArchive 类](../mfc/reference/carchive-class.md)确保所有数据都以相同格式保存。 它使用 `CArchive` 对象作为转换器。 在调用[CArchive：： Close](../mfc/reference/carchive-class.md#close)之前，此对象会一直保留在创建它的时间。 此方法可由程序员显式调用，或在程序退出包含 `CArchive`的作用域时由析构函数隐式调用。

此注释描述 `CArchive` 成员[CArchive：： ReadObject](../mfc/reference/carchive-class.md#readobject)和[CArchive：： WriteObject](../mfc/reference/carchive-class.md#writeobject)的实现。 你将在 Arcobj 中找到这些函数的代码，并在 Arccore 中找到 `CArchive` 的主要实现。 用户代码不会直接调用 `ReadObject` 和 `WriteObject`。 相反，这些对象由 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏自动生成的类特定类型安全的插入和提取运算符使用。 下面的代码演示如何隐式调用 `WriteObject` 和 `ReadObject`：

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

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>将对象保存到存储区（CArchive：： WriteObject）

方法 `CArchive::WriteObject` 写入用于重新构造对象的标头数据。 此数据由两部分组成：对象的类型和对象的状态。 此方法还负责维护要写出的对象的标识，以便仅保存单个副本，而不考虑指向该对象的指针（包括循环指针）的数目。

保存（插入）和还原（提取）对象依赖于多个 "清单常量"。 这些值存储在二进制文件中，并为存档提供重要信息（请注意，"w" 前缀表示16位数量）：

|标记|说明|
|---------|-----------------|
|wNullTag|用于 NULL 对象指针（0）。|
|wNewClassTag|指示后面的类说明是此存档上下文的新增内容（-1）。|
|wOldClassTag|指示已在此上下文（0x8000）中查看要读取的对象的类。|

存储对象时，存档维护[CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) （ *m_pStoreMap*），这是从存储的对象到32位永久性标识符（PID）的映射。 PID 分配给每个唯一对象，以及保存在存档上下文中的每个唯一类名称。 这些 Pid 按顺序从1开始。 这些 Pid 在存档范围之外没有任何意义，特别是不会与记录号或其他标识项混淆。

在 `CArchive` 类中，Pid 为32位，但它们写出为16位，除非它们大于0x7FFE。 大 Pid 编写为0x7FFF 后跟32位 PID。 这可保持与在早期版本中创建的项目的兼容性。

当请求将对象保存到存档时（通常使用全局插入运算符），会对 NULL [CObject](../mfc/reference/cobject-class.md)指针进行检查。 如果指针为 NULL，则会将*wNullTag*插入到存档流中。

如果指针不为 NULL，并且可以进行序列化（类是 `DECLARE_SERIAL` 类），则代码将检查*m_pStoreMap*以查看是否已保存该对象。 如果已存在，则代码会将与该对象关联的32位 PID 插入到存档流中。

如果尚未保存对象，则可以考虑以下两种可能性：对象和对象的精确类型（即，类）是此存档上下文的新的，或者该对象的类型已经存在。 若要确定是否已检测到该类型，代码将查询与要保存的对象相关联的[`CRuntimeClass` 对象的](../mfc/reference/cruntimeclass-structure.md) *m_pStoreMap* 。 如果存在匹配项，`WriteObject` 将插入一个标记，该标记是*wOldClassTag*和此索引的逐位 `OR`。 如果 `CRuntimeClass` 是此存档上下文的新的，`WriteObject` 会向该类分配新的 PID，并将其插入到存档中，并在其前面加上*wNewClassTag*值。

然后，使用 `CRuntimeClass::Store` 方法将此类的描述符插入到存档中。 `CRuntimeClass::Store` 插入类的架构编号（见下文）和类的 ASCII 文本名称。 请注意，使用 ASCII 文本名称并不保证跨应用程序进行存档的唯一性。 因此，您应该标记数据文件以防止损坏。 在插入类信息之后，存档会将对象放入*m_pStoreMap*中，然后调用 `Serialize` 方法来插入特定于类的数据。 在调用 `Serialize` 之前将对象放入*m_pStoreMap*会阻止将对象的多个副本保存到存储区。

返回初始调用方（通常是对象的网络的根）时，必须调用[CArchive：： Close](../mfc/reference/carchive-class.md#close)。 如果计划执行其他[CFile](../mfc/reference/cfile-class.md)操作，则必须调用 `CArchive` 方法[Flush](../mfc/reference/carchive-class.md#flush) ，以防止存档损坏。

> [!NOTE]
>  此实现对每个存档上下文的0x3FFFFFFE 索引施加硬限制。 此数字表示可以保存在单个存档中的唯一对象和类的最大数目，但单个磁盘文件可以具有无限数量的存档上下文。

## <a name="loading-objects-from-the-store-carchivereadobject"></a>正在从存储区加载对象（CArchive：： ReadObject）

加载（提取）对象使用 `CArchive::ReadObject` 方法，与 `WriteObject`相反。 与 `WriteObject`一样，`ReadObject` 不会由用户代码直接调用;用户代码应调用与预期 `CRuntimeClass`调用 `ReadObject` 的类型安全提取运算符。 这确保了提取操作的类型完整性。

由于 `WriteObject` 实现已分配了 Pid，从1开始（0是预定义为 NULL 对象），因此 `ReadObject` 实现可以使用数组来维护存档上下文的状态。 从存储中读取 PID 时，如果 PID 大于*m_pLoadArray*的当前上限，则 `ReadObject` 知道新的对象（或类说明）如下所示。

## <a name="schema-numbers"></a>架构编号

当遇到类的 `IMPLEMENT_SERIAL` 方法时，将分配给类的架构号是类实现的 "版本"。 架构是指类的实现，而不是对指定对象已被赋予持久的次数（通常称为对象版本）的实现。

如果你打算在一段时间内维护同一个类的多个不同实现，则在你修改对象的 `Serialize` 方法实现时，将使架构递增，使你能够编写代码，以便加载使用较旧版本的实现存储的对象。

当 `CArchive::ReadObject` 方法遇到持久性存储区中不同于内存中类说明的架构号的架构号时，将引发[CArchiveException](../mfc/reference/carchiveexception-class.md) 。 从此异常中恢复并不容易。

您可以将 `VERSIONABLE_SCHEMA` 与（位**或**）架构版本结合使用，以防止引发此异常。 通过使用 `VERSIONABLE_SCHEMA`，你的代码可以通过检查[CArchive：： GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema)中的返回值，在其 `Serialize` 函数中执行相应的操作。

## <a name="calling-serialize-directly"></a>直接调用序列化

在许多情况下，`WriteObject` 和 `ReadObject` 的常规对象存档方案的开销并不是必需的。 这是将数据序列化为[CDocument](../mfc/reference/cdocument-class.md)的常见情况。 在这种情况下，将直接调用 `CDocument` 的 `Serialize` 方法，而不是提取或插入运算符。 文档内容可能会依次使用更常规的对象存档方案。

直接调用 `Serialize` 具有以下优点和缺点：

- 序列化对象之前或之后，不会向存档添加额外的字节。 这不仅会使保存的数据更小，而且允许实现可处理任何文件格式 `Serialize` 例程。

- MFC 经过优化，因此，不会将 `WriteObject` 和 `ReadObject` 实现以及相关集合链接到应用程序中，除非需要更通用的对象存档方案用于其他目的。

- 你的代码不必从旧的架构编号恢复。 这会使文档序列化代码对架构号、文件格式版本号或在数据文件开头使用的任何识别号进行编码。

- 使用对 `Serialize` 的直接调用而序列化的任何对象都不得使用 `CArchive::GetObjectSchema` 或必须处理返回值（UINT）-1，指示版本未知。

由于 `Serialize` 是直接在文档上调用的，因此，文档的子对象通常不可能存档对其父文档的引用。 必须为这些对象显式提供指向其容器文档的指针，或者必须使用[CArchive：： MapObject](../mfc/reference/carchive-class.md#mapobject)函数将 `CDocument` 指针映射到 PID，然后再对其进行存档。

如前文所述，您应该在直接调用 `Serialize` 时，自行编码版本和类信息，使您可以在以后更改格式，同时仍保持与旧文件的向后兼容性。 在直接序列化对象之前或调用基类之前，可以显式调用 `CArchive::SerializeClass` 函数。

## <a name="see-also"></a>另请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
