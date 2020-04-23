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
ms.openlocfilehash: 66d76e0062d13b2bd5a16d9b07f99db9e989805a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753989"
---
# <a name="cobject-class"></a>CObject 类

Microsoft 基础类库中的主体基类。

## <a name="syntax"></a>语法

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>成员

### <a name="protected-constructors"></a>受保护的构造函数

|名称|说明|
|----------|-----------------|
|[CObject：CObject](#cobject)|默认构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CObject：：断言有效](#assertvalid)|验证此对象的完整性。|
|[CObject：:Dump](#dump)|生成此对象的诊断转储。|
|[CObject：获取运行时类](#getruntimeclass)|返回与此`CRuntimeClass`对象的类对应的结构。|
|[对象：：是](#iskindof)|测试此对象与给定类的关系。|
|[CObject：可序列化](#isserializable)|测试此对象是否可以序列化。|
|[CObject：序列化](#serialize)|从/存储从存档的对象。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CObject：：运算符删除](#operator_delete)|特殊**删除**运算符。|
|[CObject：：运算符新](#operator_new)|特殊**新**操作员。|

## <a name="remarks"></a>备注

它不仅用作库类（如`CFile`和`CObList`）的根，还充当您编写的类的根。 `CObject`提供基本服务，包括

- 序列化支持

- 运行时类信息

- 对象诊断输出

- 与集合类的兼容性

请注意，`CObject`不支持多重继承。 派生类只能有一个`CObject`基类，`CObject`并且必须在层次结构中保留最起。 但是，在右侧多继承分支中具有结构和非`CObject`派生类是允许的。

如果在类实现和声明中使用`CObject`一些可选宏，您将从派生中获得主要好处。

第一级宏[（DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)和[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)）允许运行时访问类名称及其在层次结构中的位置。 这反过来又允许有意义的诊断转储。

第二级宏[（DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)）包括第一级宏的所有功能，它们使对象能够"序列化"到"存档"和"存档"。

有关派生 Microsoft 基础类和C++类以及使用`CObject`的信息，请参阅使用[CObject](../../mfc/using-cobject.md)和[序列化](../../mfc/serialization-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CObject`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cobjectassertvalid"></a><a name="assertvalid"></a>CObject：：断言有效

验证此对象的完整性。

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>备注

`AssertValid`通过检查此对象的内部状态，对此对象执行有效性检查。 在库的调试版本中，`AssertValid`可能会断言并因此终止程序，该消息列出了断言失败的行号和文件名。

编写自己的类时，应重写该`AssertValid`函数，以便为自己和类的其他用户提供诊断服务。 重写`AssertValid`通常调用其基类`AssertValid`的函数，然后再检查派生类独有的数据成员。

由于`AssertValid`是**const**函数，因此不允许在测试期间更改对象状态。 您自己的派生类`AssertValid`函数不应引发异常，而应断言它们是否检测到无效的对象数据。

"有效性"的定义取决于对象的类。 通常，该函数应执行"浅检查"。 也就是说，如果对象包含指向其他对象的指针，则应检查指针是否为空，但不应对指针引用的对象执行有效性测试。

### <a name="example"></a>示例

有关所有`CAge``CObject`示例中使用的类的列表，请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

有关另一个示例，请参阅[AfxDoForall 对象](diagnostic-services.md#afxdoforallobjects)。

## <a name="cobjectcobject"></a><a name="cobject"></a>CObject：CObject

这些函数是标准`CObject`构造函数。

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>参数

*对象Src*<br/>
对另一个引用`CObject`

### <a name="remarks"></a>备注

派生类的构造函数会自动调用默认版本。

如果类是可序列化的（它包含IMPLEMENT_SERIAL宏），则类声明中必须有一个默认构造函数（没有参数的构造函数）。 如果不需要默认构造函数，则声明私有或受保护的"空"构造函数。 有关详细信息，请参阅使用[CObject](../../mfc/using-cobject.md)。

标准C++默认类复制构造函数执行逐个成员复制。 如果需要类的副本构造函数`CObject`但不可用，则私有复制构造函数的存在可确保编译器错误消息。 因此，如果类需要此功能，则必须提供复制构造函数。

### <a name="example"></a>示例

`CAge`有关`CObject`示例中使用的类的列表，请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

## <a name="cobjectdump"></a><a name="dump"></a>CObject：:Dump

将对象的内容转储到[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象。

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>参数

*直流*<br/>
用于转储的诊断转储上下文，通常`afxDump`为 。

### <a name="remarks"></a>备注

编写自己的类时，应重写该`Dump`函数，以便为自己和类的其他用户提供诊断服务。 重写`Dump`通常调用其基类`Dump`的函数，然后再打印派生类独有的数据成员。 `CObject::Dump`如果类使用 或 IMPLEMENT_SERIAL宏，`IMPLEMENT_DYNAMIC`请打印类名称。

> [!NOTE]
> 函数`Dump`不应在其输出结束时打印新线字符。

`Dump`仅在 Microsoft 基础类库的调试版本中才有意义。 应用 **#ifdef_DEBUG**/ `#endif`语句来括号调用、函数声明和函数实现，以便进行条件编译。

由于`Dump`是**const**函数，因此不允许在转储期间更改对象状态。

插入`CObject`指针时[，CDumpContext 插入（<<）运算符](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt)调用`Dump`。

`Dump`只允许"循环"倾倒物体。 例如，您可以转储对象列表，但如果其中一个对象是列表本身，则最终将溢出堆栈。

### <a name="example"></a>示例

有关所有`CAge``CObject`示例中使用的类的列表，请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

## <a name="cobjectgetruntimeclass"></a><a name="getruntimeclass"></a>CObject：获取运行时类

返回与此`CRuntimeClass`对象的类对应的结构。

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>返回值

指向与此对象的类对应的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的指针;从不**NULL**。

### <a name="remarks"></a>备注

每个`CObject`派生类`CRuntimeClass`有一个结构。 结构成员如下：

- **LPCSTR m_lpszClassName**包含 ASCII 类名称的 null 端接字符串。

- **int m_nObjectSize**对象的大小（以字节为单位）。 如果对象具有指向已分配内存的数据成员，则不包括该内存的大小。

- **UINT m_wSchema**架构编号 （- 1 表示不可序列化类）。 有关架构编号的说明，请参阅[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

- **CObject\* （\* PASCAL m_pfnCreateObject ））** 指向创建类对象的默认构造函数的函数指针（仅在类支持动态创建时有效;否则，返回**NULL**）。

- **CRuntimeClass\* （\* PASCAL m_pfn_GetBaseClass ）（ ）** 如果应用程序动态链接到 MFC 的 AFXDLL 版本，则指向返回`CRuntimeClass`基类结构的函数的指针。

- **CRuntimeClass\* m_pBaseClass**如果应用程序静态链接到 MFC，则指向基类`CRuntimeClass`结构的指针。

此函数要求在类实现中使用[IMPLEMENT_DYNAMIC、IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dynamic)或[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。 [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) 否则，您将获得不正确的结果。

### <a name="example"></a>示例

有关所有`CAge``CObject`示例中使用的类的列表，请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

## <a name="cobjectiskindof"></a><a name="iskindof"></a>对象：：是

测试此对象与给定类的关系。

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>参数

*pClass*<br/>
指向与派生类关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构`CObject`的指针。

### <a name="return-value"></a>返回值

如果对象对应于类，则非零;否则 0。

### <a name="remarks"></a>备注

此函数测试*pClass*以查看它是指定类的对象，还是 （2） 它是派生自指定类的类的对象。 此函数仅适用于使用[DECLARE_DYNAMIC、DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dynamic)或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏[DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)声明的类。

不要广泛使用此函数，因为它会破坏C++多态性特征。 改用虚拟函数。

### <a name="example"></a>示例

有关所有`CAge``CObject`示例中使用的类的列表，请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

## <a name="cobjectisserializable"></a><a name="isserializable"></a>CObject：可序列化

测试此对象是否有资格序列化。

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>返回值

如果可以序列化此对象，则非零;否则 0。

### <a name="remarks"></a>备注

要对类进行序列化，其声明必须包含[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏，并且实现必须包含[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

> [!NOTE]
> 不要重写此函数。

### <a name="example"></a>示例

有关所有`CAge``CObject`示例中使用的类的列表，请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

## <a name="cobjectoperator-delete"></a><a name="operator_delete"></a>CObject：：运算符删除

对于库的发布版本，运算符**删除**释放运算符**new**分配的内存。

```cpp
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

在调试版本中，操作员**删除**参与旨在检测内存泄漏的分配监视方案。

如果使用代码行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

在 中的任何实现之前。CPP 文件，然后将使用**删除**的第三个版本，将文件名和行号存储在分配的块中以供以后报告。 您不必担心提供额外的参数;宏为您处理。

即使您在调试模式下不使用DEBUG_NEW，您仍然会检测到泄漏检测，但没有上述源文件行号报告。

如果重写运算符**新****并删除**，将丧失此诊断功能。

### <a name="example"></a>示例

`CAge`有关`CObject`示例中使用的类的列表，请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

## <a name="cobjectoperator-new"></a><a name="operator_new"></a>CObject：：运算符新

对于库的发布版本，运算符**new**以类似于 的方式执行最佳内存分配`malloc`。

```cpp
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>备注

在调试版本中 **，新操作员**参与旨在检测内存泄漏的分配监视方案。

如果使用代码行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

在 中的任何实现之前。CPP 文件，然后将使用**new**的第二个版本，将文件名和行号存储在分配的块中以供以后报告。 您不必担心提供额外的参数;宏为您处理。

即使您在调试模式下不使用DEBUG_NEW，您仍然会检测到泄漏检测，但没有上述源文件行号报告。

> [!NOTE]
> 如果重写此运算符，则还必须重写**删除**。 不要使用标准库`_new_handler`函数。

### <a name="example"></a>示例

`CAge`有关`CObject`示例中使用的类的列表，请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

## <a name="cobjectserialize"></a><a name="serialize"></a>CObject：序列化

从存档读取该对象或将该对象写入存档。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
要`CArchive`序列化到或从中序列化的对象。

### <a name="remarks"></a>备注

您必须重写`Serialize`要序列化的每个类。 重写`Serialize`必须首先调用其基类`Serialize`的函数。

还必须在类声明中使用[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏，并且必须在实现中使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。

使用[CArchive：：正在加载](../../mfc/reference/carchive-class.md#isloading)或[CArchive：正在存储](../../mfc/reference/carchive-class.md#isstoring)以确定存档是加载还是存储。

`Serialize`由[CArchive 调用：读取对象](../../mfc/reference/carchive-class.md#readobject)和[CArchive：：写入对象](../../mfc/reference/carchive-class.md#writeobject)。 这些函数与`CArchive`插入运算符 （ ** < **） 和提取运算符 （ ）**>>** 相关联。

有关序列化示例，请参阅文章[序列化：序列化对象](../../mfc/serialization-serializing-an-object.md)。

### <a name="example"></a>示例

有关所有`CAge``CObject`示例中使用的类的列表，请参阅[CObList：CObList。](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)
