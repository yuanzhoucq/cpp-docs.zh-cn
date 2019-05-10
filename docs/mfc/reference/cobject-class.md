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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388314"
---
# <a name="cobject-class"></a>CObject 类

Microsoft 基础类库中的主体基类。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|描述|
|----------|-----------------|
|[CObject::CObject](#cobject)|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CObject::AssertValid](#assertvalid)|验证此对象的完整性。|
|[CObject::Dump](#dump)|生成此对象的诊断转储。|
|[CObject::GetRuntimeClass](#getruntimeclass)|返回`CRuntimeClass`结构对应于此对象的类。|
|[CObject::IsKindOf](#iskindof)|测试与给定类的此对象的关系。|
|[CObject::IsSerializable](#isserializable)|测试以查看是否可以序列化此对象。|
|[CObject::Serialize](#serialize)|加载或存储一个对象从/到存档。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CObject::operator delete](#operator_delete)|特殊**删除**运算符。|
|[新 CObject::operator](#operator_new)|特殊**新**运算符。|

## <a name="remarks"></a>备注

它如用作不仅库类的根`CFile`和`CObList`，但也为您编写的类。 `CObject` 提供基本服务，包括

- 序列化支持

- 运行时类信息

- 对象诊断输出

- 与集合类的兼容性

请注意，`CObject`不支持多重继承。 在派生的类只能有一个`CObject`基类，并且`CObject`必须为层次结构中最左侧。 它是允许的但是，有的结构和非- `CObject`-右侧的多重继承分支中派生类。

将实现从的主要好处`CObject`派生，如果您使用某些类实现和声明中的可选宏。

第一级别宏[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)并[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)，允许运行时访问类名称和层次结构中的位置。 这反过来允许有意义的诊断转储。

第二级别宏[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)并[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)，包括所有功能的第一级别宏，并且它们使对象可以"序列化"到和从"存档"。

有关 Microsoft 基础类派生信息和C++类在一般情况下，并使用`CObject`，请参阅[使用 CObject](../../mfc/using-cobject.md)并[序列化](../../mfc/serialization-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CObject`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="assertvalid"></a>  CObject::AssertValid

验证此对象的完整性。

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>备注

`AssertValid` 通过检查其内部状态执行对此对象的有效性检查。 在库的调试版本中`AssertValid`可能断言并因此终止断言失败的程序列出的行号和文件名的消息。

在编写您自己的类时，应重写`AssertValid`函数以提供您和您的类的其他用户的诊断服务。 重写`AssertValid`通常调用`AssertValid`之前检查数据成员的唯一的派生类及其基类的函数。

因为`AssertValid`是**const**函数，则不允许在测试期间更改对象状态。 派生的类`AssertValid`函数不应引发异常但而是应断言它们是否检测到无效的对象数据。

"有效性"的定义取决于对象的类。 通常，该函数应执行"浅表检查"。 也就是说，如果对象包含指向其他对象的指针，它应检查以查看是否指针不为 null，但它不应执行引用的指针对象上进行测试的有效性。

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`类中所有使用`CObject`示例。

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

有关其他示例，请参阅[AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects)。

##  <a name="cobject"></a>  CObject::CObject

这些函数是标准`CObject`构造函数。

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>参数

*objectSrc*<br/>
对另一个的引用 `CObject`

### <a name="remarks"></a>备注

在派生类的构造函数自动调用的默认版本。

如果您的类是可序列化 （它集成了 IMPLEMENT_SERIAL 宏），则必须在类声明具有默认构造函数 （不带任何参数的构造函数）。 如果不需要默认构造函数，声明一个私有或受保护"空"的构造函数。 有关详细信息，请参阅[使用 CObject](../../mfc/using-cobject.md)。

标准C++默认类的复制构造函数 does 成员按成员复制。 是否存在私有`CObject`复制构造函数可保证编译器错误消息，如果您的类的复制构造函数是所需但不可用。 如果您的类时要求此功能，因此必须提供一个复制构造函数。

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`类中使用`CObject`示例。

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

##  <a name="dump"></a>  CObject::Dump

到对象的内容转储[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象。

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>参数

*dc*<br/>
转储，通常的诊断转储上下文`afxDump`。

### <a name="remarks"></a>备注

在编写您自己的类时，应重写`Dump`函数以提供您和您的类的其他用户的诊断服务。 重写`Dump`通常调用`Dump`打印唯一的派生类的数据成员之前其基本类的函数。 `CObject::Dump` 如果您的类使用打印的类名`IMPLEMENT_DYNAMIC`或 IMPLEMENT_SERIAL 宏。

> [!NOTE]
>  你`Dump`函数不应打印其输出末尾处换行字符。

`Dump` 调用仅在 Microsoft 基础类库的调试版本中有意义。 调用、 函数声明和使用的函数实现应方括号 **#ifdef _DEBUG** /  `#endif`进行条件编译的语句。

由于`Dump`是**const**函数，则不允许在转储过程中更改对象状态。

[CDumpContext 插入 (<<) 运算符](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt)调用`Dump`时`CObject`插入指针。

`Dump` 允许仅"有向无环"转储的对象。 例如，您可以转储一系列对象，但如果该列表本身的对象之一，您将最终堆栈溢出。

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`类中所有使用`CObject`示例。

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

##  <a name="getruntimeclass"></a>  CObject::GetRuntimeClass

返回`CRuntimeClass`结构对应于此对象的类。

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>返回值

一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构对应于此对象的类; 永远不会**NULL**。

### <a name="remarks"></a>备注

还有一个`CRuntimeClass`为每个结构`CObject`-派生的类。 结构成员是按如下所示：

- **LPCSTR m_lpszClassName**包含 ASCII 类名的以 null 结尾的字符串。

- **int m_nObjectSize**对象，以字节为单位的大小。 如果对象具有数据成员指向已分配的内存的则不包含该内存的大小。

- **UINT m_wSchema**架构数字 (-1 表示不可序列化类)。 请参阅[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)有关的架构数字说明的宏。

- **CObject\* (PASCAL\* m_pfnCreateObject) （)** 创建您的类的对象的默认构造函数的函数指针 (有效仅当类支持动态创建; 否则，返回**NULL**).

- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) （)** 如果你的应用程序动态链接到 MFC 的 AFXDLL 版本中，指向函数的返回`CRuntimeClass`结构的基类。

- **CRuntimeClass\* m_pBaseClass**如果你的应用程序静态链接到 MFC，一个指向`CRuntimeClass`结构的基类。

此函数需要使用[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)， [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)，或[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)类实现中的宏。 否则，您将得到不正确的结果。

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`类中所有使用`CObject`示例。

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

##  <a name="iskindof"></a>  CObject::IsKindOf

测试与给定类的此对象的关系。

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>参数

*pClass*<br/>
一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与关联的结构在`CObject`-派生的类。

### <a name="return-value"></a>返回值

如果该对象对应于类; 非零值否则为 0。

### <a name="remarks"></a>备注

此函数将测试*pClass* （1） 它是指定类的对象或者 （2） 它是派生自指定类的类的对象。 此函数仅适用于使用声明的类[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)， [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)，或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏。

不要使用此函数广泛因为它使您无法获得C++多形性功能。 而是使用虚函数。

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`类中所有使用`CObject`示例。

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

##  <a name="isserializable"></a>  CObject::IsSerializable

测试此对象是否符合条件的序列化。

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>返回值

如果此对象可序列化; 非零值否则为 0。

### <a name="remarks"></a>备注

必须是可序列化的类，包含其声明[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏，并实现必须包含[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

> [!NOTE]
>  不会覆盖此函数。

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`类中所有使用`CObject`示例。

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

##  <a name="operator_delete"></a>  CObject::operator delete

发布版本的库，运算符**删除**释放运算符分配的内存**新**。

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

在调试版本中，运算符**删除**参与设计用于检测内存泄漏的分配监视方案。

如果使用的代码行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

在您的实现中的任何前。CPP 文件，然后第三个版本的**删除**将使用，在更高版本报告的已分配块中存储的文件名和行号。 无需担心如何提供额外的参数;宏会负责。

即使在调试模式下不使用 DEBUG_NEW，仍获取泄漏检测，但没有源文件行号 reporting 上面所述。

如果重写运算符**新**并**删除**，丧失此诊断功能。

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`类中使用`CObject`示例。

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

##  <a name="operator_new"></a>  新 CObject::operator

发布版本的库，运算符**新**执行类似的方式实现最佳的内存分配`malloc`。

```
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>备注

在调试版本中，运算符**新**参与设计用于检测内存泄漏的分配监视方案。

如果使用的代码行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

在您的实现中的任何前。CPP 文件，然后第二个版本的**新**将使用，在更高版本报告的已分配块中存储的文件名和行号。 无需担心如何提供额外的参数;宏会负责。

即使在调试模式下不使用 DEBUG_NEW，仍获取泄漏检测，但没有源文件行号 reporting 上面所述。

> [!NOTE]
>  如果重写此运算符，则还必须重写**删除**。 不使用标准库`_new_handler`函数。

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`类中使用`CObject`示例。

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

##  <a name="serialize"></a>  CObject::Serialize

从存档读取该对象或将该对象写入存档。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
一个`CArchive`要面向或源自序列化对象。

### <a name="remarks"></a>备注

必须重写`Serialize`所要序列化每个类。 重写`Serialize`必须先调用`Serialize`其基类的函数。

此外必须使用[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏在类声明中，并且您必须使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏的实现中。

使用[CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading)或[CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring)来确定存档是否已加载或存储。

`Serialize` 调用[CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject)并[CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject)。 这些函数与相关联`CArchive`插入运算符 ( **< \<**) 和提取运算符 ( **>>**)。

有关序列化示例，请参阅文章[序列化：将对象序列化为](../../mfc/serialization-serializing-an-object.md)。

### <a name="example"></a>示例

请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`类中所有使用`CObject`示例。

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)
