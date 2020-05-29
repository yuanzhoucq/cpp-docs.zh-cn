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
ms.openlocfilehash: f65a7b7afcf6bd832c9c23560bb29374038fae1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370443"
---
# <a name="tn002-persistent-object-data-format"></a>TN002：持久性对象数据格式

本注释介绍支持持久C++对象的 MFC 例程，以及对象数据存储在文件中时的格式。 这仅适用于具有[DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial)宏的类。

## <a name="the-problem"></a>问题

持久数据的 MFC 实现将许多对象的数据存储在文件的单个连续部分。 对象`Serialize`的方法将对象的数据转换为紧凑的二进制格式。

实现保证通过使用[CArchive 类](../mfc/reference/carchive-class.md)以相同的格式保存所有数据。 它使用`CArchive`对象作为转换器。 此对象从创建时一直持续到调用[CArchive：：：关闭](../mfc/reference/carchive-class.md#close)。 当程序退出包含 的范围时，程序员可以显式调用此方法，也可以由析构函数隐式调用`CArchive`此方法。

本说明描述了`CArchive`成员[CArchive：：读取对象](../mfc/reference/carchive-class.md#readobject)和[CArchive：：WriteObject](../mfc/reference/carchive-class.md#writeobject)的实现。 您可以在 Arcobj.cpp 中找到这些函数的代码，以及 Arccore.cpp`CArchive`中的主要实现。 用户代码不直接调用`ReadObject`和`WriteObject`调用。 相反，这些对象由特定于类的类型安全插入和提取运算符使用，这些运算符由DECLARE_SERIAL和IMPLEMENT_SERIAL宏自动生成。 以下代码显示如何`WriteObject`和`ReadObject`隐式调用：

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

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>将对象保存到存储（CArchive：：写入对象）

该方法`CArchive::WriteObject`写入用于重建对象的标头数据。 此数据由两部分组成：对象的类型和对象的状态。 此方法还负责维护正在写入的对象的标识，以便只保存单个副本，而不考虑指向该对象的指针数（包括循环指针）。

保存（插入）和还原（提取）对象依赖于多个"清单常量"。 这些值以二进制方式存储，并且向存档提供重要信息（请注意，"w"前缀表示 16 位数量）：

|标记|说明|
|---------|-----------------|
|wNullTag|用于 NULL 对象指针 （0）。|
|wNewClassTag|指示后面的类描述是此存档上下文 （-1） 的新增内容说明。|
|wOldClassTag|指示在此上下文中 （0x8000） 已看到正在读取的对象的类。|

存储对象时，存档维护一个[CMapPtrToPtr（m_pStoreMap），](../mfc/reference/cmapptrtoptr-class.md)它是从存储的对象映射到 32 位持久标识符 （PID）。 *m_pStoreMap* PID 分配给保存在存档上下文中的每个唯一对象和每个唯一类名称。 这些 PID 从 1 开始按顺序分发。 这些 PID 在存档范围之外没有意义，尤其不应与记录编号或其他标识项混淆。

在类`CArchive`中，PID 是 32 位，但它们被写成 16 位，除非它们大于 0x7FFE。 大型 PID 编写为 0x7FFF，后跟 32 位 PID。 这将保持与在早期版本中创建的项目的兼容性。

当请求将对象保存到存档时（通常使用全局插入运算符），将检查 NULL [CObject](../mfc/reference/cobject-class.md)指针。 如果指针为 NULL，则*wNullTag*将插入到存档流中。

如果指针不是 NULL 并且可以序列化（类是`DECLARE_SERIAL`类），则代码将检查*m_pStoreMap*以查看对象是否已保存。 如果有，代码将与该对象关联的 32 位 PID 插入到存档流中。

如果对象以前未保存，则有两种可能性需要考虑：对象和对象的确切类型（即类）都是此存档上下文的新类型，或者对象是已看到的确切类型。 要确定是否已看到该类型，代码会查询与要保存`CRuntimeClass`的对象关联的对象的[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)对象的*m_pStoreMap。* 如果存在匹配项，则`WriteObject`插入*wOldClassTag*和此索引的`OR`位标记。 如果`CRuntimeClass`是此存档上下文的新增，`WriteObject`请向该类分配新的 PID 并将其插入到存档中，前面是*wNewClassTag*值。

然后，使用 方法`CRuntimeClass::Store`将此类的描述符插入到存档中。 `CRuntimeClass::Store`插入类的架构编号（见下文）和类的 ASCII 文本名称。 请注意，使用 ASCII 文本名称并不保证整个应用程序存档的唯一性。 因此，您应该标记数据文件以防止损坏。 插入类信息后，存档将对象放入*m_pStoreMap，* 然后调用`Serialize`方法插入特定于类的数据。 在调用`Serialize`之前将对象放入*m_pStoreMap*可防止将对象的多个副本保存到存储中。

返回到初始调用方（通常是对象网络的根），必须调用[CArchive：：：关闭](../mfc/reference/carchive-class.md#close)。 如果计划执行其他[CFile](../mfc/reference/cfile-class.md)操作，则必须调用`CArchive`["刷新"](../mfc/reference/carchive-class.md#flush)方法以防止存档损坏。

> [!NOTE]
> 此实现对每个存档上下文的 0x3FFFFE 索引施加了硬限制。 此数字表示可保存在单个存档中的最大唯一对象和类数，但单个磁盘文件可以具有无限数量的存档上下文。

## <a name="loading-objects-from-the-store-carchivereadobject"></a>从存储加载对象（CArchive：：读取对象）

加载（提取）对象使用 方法`CArchive::ReadObject`，与 相反`WriteObject`。 与`WriteObject`一`ReadObject`样，用户代码不直接调用 ;用户代码应调用`ReadObject`使用预期的`CRuntimeClass`类型安全提取运算符。 这将确保数据提取操作的类型完整性。

由于`WriteObject`分配的实现不断增加 PID，从 1 开始（0 预定义为 NULL 对象），实现`ReadObject`可以使用数组来维护存档上下文的状态。 从存储中读取 PID 时，如果 PID 大于*m_pLoadArray*的当前上限，`ReadObject`则知道将遵循新对象（或类描述）。

## <a name="schema-numbers"></a>架构编号

遇到类`IMPLEMENT_SERIAL`的方法时分配给类的架构编号是类实现的"版本"。 架构是指类的实现，而不是给定对象被持久化的次数（通常称为对象版本）。

如果打算随着时间的推移维护同一类的几个不同实现，则在修改对象`Serialize`的方法实现时增加架构将使您能够编写代码，这些代码可以使用旧版本的实现加载存储的对象。

`CArchive::ReadObject`当该方法在持久存储中遇到与内存中类描述的架构编号不同的架构编号时，将引发[CArchiveException。](../mfc/reference/carchiveexception-class.md) 要从此异常中恢复并不容易。

您可以使用 （`VERSIONABLE_SCHEMA`位**或**） 架构版本来防止引发此异常。 通过使用`VERSIONABLE_SCHEMA`，您的代码可以通过检查`Serialize`[CArchive：：getObjectSchema](../mfc/reference/carchive-class.md#getobjectschema)中的返回值来在其函数中采取适当的操作。

## <a name="calling-serialize-directly"></a>直接调用序列化

在许多情况下，一般对象存档方案的开销`WriteObject``ReadObject`是没有必要的。 这是将数据序列化到[CDocument](../mfc/reference/cdocument-class.md)的常见情况。 在这种情况下，`Serialize`直接调用 的方法`CDocument`，而不是使用提取或插入运算符调用。 文档的内容可能反过来使用更通用的对象存档方案。

直接`Serialize`调用有以下优点和缺点：

- 在对象序列化之前或之后，不会向存档添加额外的字节。 这不仅使保存的数据变小，还允许您实现`Serialize`可以处理任何文件格式的例程。

- MFC 已调整，因此`WriteObject`，`ReadObject`除非出于其他目的需要更通用的对象存档方案，否则 不会将 和 实现和相关集合链接到您的应用程序中。

- 您的代码不必从旧的架构编号中恢复。 这使文档序列化代码负责对架构码、文件格式版本号或数据文件开头使用的任何标识编号进行编码。

- 使用直接调用序列化的任何对象`Serialize`不得使用`CArchive::GetObjectSchema`或必须处理 （UINT）-1 的返回值，指示版本未知。

由于`Serialize`直接在文档上调用，因此文档的子对象通常无法存档对其父文档的引用。 必须显式为这些对象提供指向其容器文档的指针，否则您必须使用[CArchive：mapObject](../mfc/reference/carchive-class.md#mapobject)函数将这些`CDocument`指针映射到 PID，然后才能存档这些回指针。

如前所述，在直接调用`Serialize`时，应自行对版本和类信息进行编码，以便以后更改格式，同时仍与旧文件保持向后兼容性。 可以直接`CArchive::SerializeClass`序列化对象之前或调用基类之前，可以显式调用该函数。

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
