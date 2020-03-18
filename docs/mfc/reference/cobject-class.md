---
title: CObject 类
ms.date: 11/04/2016
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
ms.openlocfilehash: 515c4e90ee6ab77a6c7c1ae108393ea1aafb7c17
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424019"
---
# <a name="cobject-class"></a>CObject 类

Microsoft 基础类库中的主体基类。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护构造函数

|名称|说明|
|----------|-----------------|
|[CObject：： CObject](#cobject)|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CObject：： AssertValid](#assertvalid)|验证此对象的完整性。|
|[CObject：:D ump](#dump)|生成此对象的诊断转储。|
|[CObject：： GetRuntimeClass](#getruntimeclass)|返回与此对象的类相对应的 `CRuntimeClass` 结构。|
|[CObject：： IsKindOf](#iskindof)|测试与给定类的此对象的关系。|
|[CObject：： IsSerializable](#isserializable)|测试以确定此对象是否可以序列化。|
|[CObject：：串行化](#serialize)|从/向存档中加载或存储对象。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[CObject：： operator delete](#operator_delete)|特殊**删除**运算符。|
|[CObject：： operator new](#operator_new)|特殊**new**运算符。|

## <a name="remarks"></a>备注

它不仅可用作 `CFile` 和 `CObList`等库类的根，还用作你编写的类的根。 `CObject` 提供基本的服务，包括

- 序列化支持

- 运行时类信息

- 对象诊断输出

- 与集合类的兼容性

请注意，`CObject` 不支持多重继承。 派生类只能有一个 `CObject` 基类，并且 `CObject` 必须在层次结构中位于最左侧。 但允许在右侧多继承分支中具有结构和非 `CObject`派生类。

如果在类实现和声明中使用某些可选的宏，你将能够从 `CObject` 派生中获益。

第一级宏（ [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)和[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)）允许运行时访问类名及其在层次结构中的位置。 这反过来又允许有意义的诊断转储。

第二级宏（ [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)）包含第一级宏的所有功能，并且使对象可以与 "存档" 进行 "序列化"。

有关一般派生 Microsoft 基础类和C++类和使用 `CObject`的信息，请参阅[使用 CObject](../../mfc/using-cobject.md)和[序列化](../../mfc/serialization-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CObject`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="assertvalid"></a>CObject：： AssertValid

验证此对象的完整性。

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>备注

`AssertValid` 通过检查此对象的内部状态来执行有效性检查。 在库的调试版本中，`AssertValid` 可能会断言，并因此终止程序，并提供一条消息，其中列出断言失败的行号和文件名。

编写自己的类时，应重写 `AssertValid` 函数，以便为自己和类的其他用户提供诊断服务。 重写的 `AssertValid` 通常会在检查派生类的唯一数据成员之前调用其基类的 `AssertValid` 函数。

由于 `AssertValid` 是**const**函数，因此不允许在测试期间更改对象状态。 您自己的派生类 `AssertValid` 函数不应引发异常，而应断言它们是否检测到无效的对象数据。

"有效性" 的定义取决于对象的类。 通常，此函数应执行 "浅检查"。 也就是说，如果对象包含指向其他对象的指针，它应检查指针是否不为 null，但不应对指针所引用的对象执行有效性测试。

### <a name="example"></a>示例

有关所有 `CObject` 示例中所用 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

有关其他示例，请参阅[AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects)。

##  <a name="cobject"></a>CObject：： CObject

这些函数是标准 `CObject` 构造函数。

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>parameters

*objectSrc*<br/>
对另一 `CObject` 的引用

### <a name="remarks"></a>备注

默认版本自动由派生类的构造函数调用。

如果你的类可序列化（它包含 IMPLEMENT_SERIAL 宏），则你必须在类声明中有一个默认构造函数（没有参数的构造函数）。 如果不需要默认构造函数，请声明私有或受保护的 "empty" 构造函数。 有关详细信息，请参阅[使用 CObject](../../mfc/using-cobject.md)。

标准C++默认类复制构造函数执行成员成员复制。 如果需要类的复制构造函数但该构造函数不可用，则私有 `CObject` 复制构造函数的存在可保证编译器错误消息。 因此，你必须提供复制构造函数（如果你的类需要此功能）。

### <a name="example"></a>示例

有关 `CObject` 示例中所用 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

##  <a name="dump"></a>CObject：:D ump

将对象的内容转储到[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象。

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>parameters

*dc*<br/>
用于转储的诊断转储上下文，通常 `afxDump`。

### <a name="remarks"></a>备注

编写自己的类时，应重写 `Dump` 函数，以便为自己和类的其他用户提供诊断服务。 重写的 `Dump` 通常会在输出派生类的唯一数据成员之前调用其基类的 `Dump` 函数。 如果类使用 `IMPLEMENT_DYNAMIC` 或 IMPLEMENT_SERIAL 宏，`CObject::Dump` 打印类名。

> [!NOTE]
>  `Dump` 函数不应在输出的末尾处打印换行符。

`Dump` 调用仅在 Microsoft 基础类库的调试版本中才有意义。 应将调用、函数声明和函数实现放在一起，将 **#ifdef _DEBUG**/ 条件编译的 `#endif` 语句中。

由于 `Dump` 是**const**函数，因此不允许在转储期间更改对象状态。

插入 `CObject` 指针时， [CDumpContext 插入（< <）运算符](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt)将调用 `Dump`。

`Dump` 只允许对象的 "非循环" 转储。 例如，你可以转储对象列表，但如果其中一个对象是列表本身，则最终会使堆栈溢出。

### <a name="example"></a>示例

有关所有 `CObject` 示例中所用 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

##  <a name="getruntimeclass"></a>CObject：： GetRuntimeClass

返回与此对象的类相对应的 `CRuntimeClass` 结构。

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>返回值

指向与此对象的类相对应的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的指针;不**为 NULL**。

### <a name="remarks"></a>备注

每个 `CObject`派生类都有一个 `CRuntimeClass` 结构。 结构成员如下所示：

- **LPCSTR m_lpszClassName**一个以 null 结尾的字符串，其中包含 ASCII 类名。

- **int m_nObjectSize**对象的大小（以字节为单位）。 如果对象具有指向已分配内存的数据成员，则不包含该内存的大小。

- **UINT m_wSchema**架构编号（对于不可序列化类，为-1）。 有关架构编号的说明，请参阅[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

- **CObject\* （PASCAL\* m_pfnCreateObject）（）** 指向创建类的对象的默认构造函数的函数指针（仅当类支持动态创建时有效; 否则，返回**NULL**）。

- **CRuntimeClass\* （PASCAL\* m_pfn_GetBaseClass）（）** 如果你的应用程序动态链接到 MFC 的 AFXDLL 版本，则返回一个指向函数的指针，该函数返回基类的 `CRuntimeClass` 结构。

- **CRuntimeClass\* m_pBaseClass**如果应用程序静态链接到 MFC，则为指向基类的 `CRuntimeClass` 结构的指针。

此函数要求在类实现中使用[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)、 [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)或[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。 否则，会得到错误的结果。

### <a name="example"></a>示例

有关所有 `CObject` 示例中所用 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

##  <a name="iskindof"></a>CObject：： IsKindOf

测试与给定类的此对象的关系。

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>parameters

*pClass*<br/>
指向与 `CObject`派生类关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的指针。

### <a name="return-value"></a>返回值

如果对象对应于类，则为非零;否则为0。

### <a name="remarks"></a>备注

此函数对*pClass*进行测试，以查看是否（1）它是指定类的对象，或（2）它是派生自指定类的类的对象。 此函数仅适用于使用[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)、 [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏声明的类。

不要广泛使用此函数，因为它会破坏C++多态性功能。 改用虚函数。

### <a name="example"></a>示例

有关所有 `CObject` 示例中所用 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

##  <a name="isserializable"></a>CObject：： IsSerializable

测试此对象是否适用于序列化。

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>返回值

如果此对象可以序列化，则为非零值;否则为0。

### <a name="remarks"></a>备注

要使类可序列化，它的声明必须包含[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏，且实现必须包含[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

> [!NOTE]
>  不要重写此函数。

### <a name="example"></a>示例

有关所有 `CObject` 示例中所用 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

##  <a name="operator_delete"></a>CObject：： operator delete

对于库的发行版，运算符**delete**释放了由运算符**new**分配的内存。

```
void PASCAL operator delete(void* p);

void PASCAL operator delete(
    void* p,
    void* pPlace);

void PASCAL operator delete(
    void* p,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>备注

在调试版本中，运算符**删除**参与了用于检测内存泄漏的分配监视方案。

如果使用代码行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

之前的任何实现。然后，将使用第三个版本的**delete** ，将文件名和行号存储在已分配的块中供以后报告。 无需担心提供额外的参数;宏负责处理此操作。

即使您在调试模式下不使用 DEBUG_NEW，仍会获得泄漏检测，但不需要上文所述的源文件行号报告。

如果重写运算符**new**和**delete**，则会使此诊断功能。

### <a name="example"></a>示例

有关 `CObject` 示例中所用 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

##  <a name="operator_new"></a>CObject：： operator new

对于库的发行版，operator **new**以类似于 `malloc`的方式执行最佳内存分配。

```
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>备注

在调试版本中，运算符**new**参与了用于检测内存泄漏的分配监视方案。

如果使用代码行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

之前的任何实现。然后，将使用第二个版本的**新**，并在分配的块中存储文件名和行号以便以后进行报告。 无需担心提供额外的参数;宏负责处理此操作。

即使您在调试模式下不使用 DEBUG_NEW，仍会获得泄漏检测，但不需要上文所述的源文件行号报告。

> [!NOTE]
>  如果重写此运算符，则还必须重写**delete**。 不要使用标准库 `_new_handler` 函数。

### <a name="example"></a>示例

有关 `CObject` 示例中所用 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

##  <a name="serialize"></a>CObject：：串行化

从存档读取该对象或将该对象写入存档。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>parameters

*ar*<br/>
要序列化到或从其进行序列化的 `CArchive` 对象。

### <a name="remarks"></a>备注

必须重写每个要序列化的类的 `Serialize`。 重写的 `Serialize` 必须先调用其基类的 `Serialize` 函数。

还必须在类声明中使用[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏，并且必须使用实现中的[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

使用[CArchive：： IsLoading](../../mfc/reference/carchive-class.md#isloading)或[Carchive：： IsStoring](../../mfc/reference/carchive-class.md#isstoring)来确定存档是否正在加载或存储。

`Serialize` 由[carchive：： ReadObject](../../mfc/reference/carchive-class.md#readobject)和[Carchive：： WriteObject](../../mfc/reference/carchive-class.md#writeobject)调用。 这些函数与 `CArchive` 插入运算符（ **<\<** ）和提取运算符（ **>>** ）相关联。

有关序列化示例，请参阅文章[序列化：序列化对象](../../mfc/serialization-serializing-an-object.md)。

### <a name="example"></a>示例

有关所有 `CObject` 示例中所用 `CAge` 类的列表，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist) 。

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)
