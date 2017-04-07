---
title: "CObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- base classes, MFC objects
- objects [C++], base class for MFC
- object classes
- CObject class
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d411b9da8618eaac57045a1db05251517422976a
ms.lasthandoff: 02/24/2017

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
|[CObject::CObject](#cobject)|默认构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CObject::AssertValid](#assertvalid)|验证此对象的完整性。|  
|[CObject::Dump](#dump)|生成此对象的诊断转储。|  
|[CObject::GetRuntimeClass](#getruntimeclass)|返回`CRuntimeClass`结构对应于此对象的类。|  
|[CObject::IsKindOf](#iskindof)|测试到给定类的此对象的关系。|  
|[CObject::IsSerializable](#isserializable)|测试以查看是否可以序列化此对象。|  
|[Cobject:: Serialize](#serialize)|加载或存储从/到存档中的对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CObject::operator delete](#operator_delete)|特殊**删除**运算符。|  
|[新的 CObject::operator](#operator_new)|特殊**新**运算符。|  
  
## <a name="remarks"></a>备注  
 它如用作不仅库类的根`CFile`和`CObList`，但还为您编写的类。 `CObject`提供基本服务，包括  
  
-   序列化支持  
  
-   运行时类信息  
  
-   对象的诊断输出  
  
-   与集合类的兼容性  
  
 请注意，`CObject`不支持多重继承。 派生的类只能有一个`CObject`基本类，并且`CObject`必须是层次结构中最左侧。 它是允许的但是，有的结构和非- `CObject`-右侧多重继承分支中派生类。  
  
 您会意识到主要受益`CObject`派生，如果您使用某些类实现和声明中的可选宏。  
  
 第一级宏[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)和[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)，允许运行时访问类名称和在层次结构中的位置。 这样，反过来，有意义的诊断转储。  
  
 第二层宏[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)，包括第一级宏的所有功能，以及它们使对象可以"序列化"与"存档"。  
  
 有关通常派生的 Microsoft 基础类和 c + + 类和使用信息`CObject`，请参阅[使用 CObject](../../mfc/using-cobject.md)和[序列化](../../mfc/serialization-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CObject`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="assertvalid"></a>CObject::AssertValid  
 验证此对象的完整性。  
  
```  
virtual void AssertValid() const;  
```  
  
### <a name="remarks"></a>备注  
 `AssertValid`通过检查其内部状态执行有效性检查对此对象。 库的调试版本中`AssertValid`可能断言并因此终止此程序包含在一条消息，其中列出行号和 filename 断言失败。  
  
 在编写您自己的类时，应重写`AssertValid`函数以提供诊断服务为你自己和您的类的其他用户。 重写`AssertValid`通常调用`AssertValid`检查派生类特有的数据成员之前其基本类的函数。  
  
 因为`AssertValid`是**const**函数，不允许你在测试过程中更改对象的状态。 在派生的类`AssertValid`函数不应引发异常，但而是应断言它们是否检测到无效的对象数据。  
  
 "有效性"的定义取决于对象的类。 通常，该函数应执行"浅表检查"。 也就是说，如果对象包含指向其他对象的指针，它应检查以查看是否指针不为 null，但不是应执行所引用的指针对象上进行测试的有效性。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)可以列出`CAge`中所有使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&7;](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]  
  
 另一个示例，请参阅[AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects)。  
  
##  <a name="cobject"></a>CObject::CObject  
 这些函数是标准`CObject`构造函数。  
  
```  
CObject();  
CObject(const CObject& objectSrc);
```  
  
### <a name="parameters"></a>参数  
 *objectSrc*  
 对另一个的引用`CObject`  
  
### <a name="remarks"></a>备注  
 在派生类的构造函数自动调用的默认版本。  
  
 如果您的类是可序列化 (它融合了`IMPLEMENT_SERIAL`宏)，则必须在类声明具有默认构造函数 （不带任何参数的构造函数）。 如果您不需要默认构造函数，声明一个私有或受保护"空"的构造函数。 有关详细信息，请参阅[使用 CObject](../../mfc/using-cobject.md)。  
  
 标准 c + + 默认类复制构造函数执行成员按成员复制。 私钥是否存在`CObject`复制构造函数可保证编译器错误消息，如果您的类的复制构造函数是所需但不可用。 如果您的类需要此功能，因此必须提供一个复制构造函数。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)可以列出`CAge`中使用的类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&8;](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]  
  
##  <a name="dump"></a>CObject::Dump  
 为您的对象的内容转储[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象。  
  
```  
virtual void Dump(CDumpContext& dc) const;  
```  
  
### <a name="parameters"></a>参数  
 `dc`  
 用于转储，通常诊断转储上下文`afxDump`。  
  
### <a name="remarks"></a>备注  
 在编写您自己的类时，应重写`Dump`函数以提供诊断服务为你自己和您的类的其他用户。 重写`Dump`通常调用`Dump`派生类特有的数据成员在打印之前其基本类的函数。 `CObject::Dump`如果您的类使用打印的类名`IMPLEMENT_DYNAMIC`或`IMPLEMENT_SERIAL`宏。  
  
> [!NOTE]
>  您`Dump`函数应该不会打印出来换行字符，其输出的末尾。  
  
 `Dump`调用仅在 Microsoft 基础类库的调试版本中有意义。 应方括号调用、 函数声明和使用的函数实现**#ifdef _DEBUG** /  `#endif`用于条件编译的语句。  
  
 由于`Dump`是**const**函数，您不允许在转储过程中更改对象的状态。  
  
 [CDumpContext 插入 (<)> </)> ](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt)调用`Dump`时`CObject`插入指针。  
  
 `Dump`允许仅"循环"转储的对象。 例如，你可以转储对象列表，但如果该列表本身的一个对象，您将最终堆栈溢出。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)可以列出`CAge`中所有使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&9;](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]  
  
##  <a name="getruntimeclass"></a>CObject::GetRuntimeClass  
 返回`CRuntimeClass`结构对应于此对象的类。  
  
```  
virtual CRuntimeClass* GetRuntimeClass() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构对应于此对象的类; 永远不会**NULL**。  
  
### <a name="remarks"></a>备注  
 没有一个`CRuntimeClass`为每个结构`CObject`的派生类。 结构成员如下所示︰  
  
- **LPCSTR m_lpszClassName**包含 ASCII 类名以 null 结尾的字符串。  
  
- **int m_nObjectSize**对象，以字节为单位的大小。 如果对象具有数据成员的指向分配的内存，则不包含该内存的大小。  
  
- **UINT m_wSchema**架构数字 (– 1 表示不可序列化的类)。 请参阅[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)有关的架构数字说明的宏。  
  
- **CObject\* (PASCAL\* m_pfnCreateObject) （)**创建您的类的对象的默认构造函数的函数指针 (有效前提的类支持动态创建; 否则，返回**NULL**)。  
  
- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) （)**如果您的应用程序动态链接到 MFC 的 AFXDLL 版本，返回指向函数的指针`CRuntimeClass`结构的基类。  
  
- **CRuntimeClass\* m_pBaseClass**如果您的应用程序静态链接到 MFC，一个指向`CRuntimeClass`结构的基类。  
  
 此函数需要使用[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)， [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)，或[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)类实现中的宏。 否则，你将收到不正确的结果。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)可以列出`CAge`中所有使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&10;](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]  
  
##  <a name="iskindof"></a>CObject::IsKindOf  
 测试到给定类的此对象的关系。  
  
```  
BOOL IsKindOf(const CRuntimeClass* pClass) const;  
```  
  
### <a name="parameters"></a>参数  
 `pClass`  
 一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)的关联结构您`CObject`的派生类。  
  
### <a name="return-value"></a>返回值  
 非零，如果该对象对应的类;否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数将测试`pClass`以查看是否 （1） 它是指定类的对象或 （2） 它是从指定的类派生的类的对象。 此函数仅适用于与声明的类[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)， [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)，或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏。  
  
 不要使用此函数广泛因为它使您无法获得 c + + 多态性功能。 而是使用虚函数。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)可以列出`CAge`中所有使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&11;](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]  
  
##  <a name="isserializable"></a>CObject::IsSerializable  
 测试此对象是否是适合序列化。  
  
```  
BOOL IsSerializable() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果此对象可以序列化;否则为 0。  
  
### <a name="remarks"></a>备注  
 对于可序列化的类，其声明必须包含[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏，而且该实现必须包含[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。  
  
> [!NOTE]
>  不会覆盖此函数。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)可以列出`CAge`中所有使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&12;](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]  
  
##  <a name="operator_delete"></a>CObject::operator delete  
 库的发行版运算符**删除**释放由运算符分配的内存**新**。  
  
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
 在调试版本中，运算符**删除**参与设计为检测内存泄漏分配监视方案。  
  
 如果您使用的代码行  
  
 [!code-cpp[NVC_MFCCObjectSample #&14;](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 在您的实现中的任何之前。CPP 文件，然后第三个版本的**删除**将使用，以便日后制作报表的已分配块中存储的文件名和行号。 无需担心如何提供额外的参数;宏负责为您的程序。  
  
 即使您不使用`DEBUG_NEW`处于调试模式，您仍然收到泄漏检测，但没有源代码文件行号 reporting 上面所述。  
  
 如果重写运算符**新**和**删除**，放弃此诊断功能。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)可以列出`CAge`中使用的类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&15;](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]  
  
##  <a name="operator_new"></a>新的 CObject::operator  
 库的发行版运算符**新**执行最佳的内存分配的方式类似于`malloc`。  
  
```  
void* PASCAL operator new(size_t nSize);  
void* PASCAL operator new(size_t, void* p);

 
void* PASCAL operator new(
    size_t nSize,  
    LPCSTR lpszFileName,  
    int nLine);
```  
  
### <a name="remarks"></a>备注  
 在调试版本中，运算符**新**参与设计为检测内存泄漏分配监视方案。  
  
 如果您使用的代码行  
  
 [!code-cpp[NVC_MFCCObjectSample #&14;](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 在您的实现中的任何之前。CPP 文件，然后第二版**新**将使用，以便日后制作报表的已分配块中存储的文件名和行号。 无需担心如何提供额外的参数;宏负责为您的程序。  
  
 即使您不使用`DEBUG_NEW`处于调试模式，您仍然收到泄漏检测，但没有源代码文件行号 reporting 上面所述。  
  
> [!NOTE]
>  如果重写此运算符，还必须重写**删除**。 不使用标准库**_new_handler**函数。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)可以列出`CAge`中使用的类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&16;](../../mfc/codesnippet/cpp/cobject-class_9.h)]  
  
##  <a name="serialize"></a>Cobject:: Serialize  
 从存档读取该对象或将该对象写入存档。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 `ar`  
 一个`CArchive`要面向或源自序列化对象。  
  
### <a name="remarks"></a>备注  
 必须重写`Serialize`为你想要序列化每个类。 重写`Serialize`必须首先调用`Serialize`其基本类的函数。  
  
 您还必须使用[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏保存在类声明中，并且您必须使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏的实现中。  
  
 使用[CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading)或[CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring)以确定加载还是存储存档。  
  
 `Serialize`由调用[CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject)和[CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject)。 这些函数与之关联`CArchive`插入运算符 ( ** < \< **) 和提取运算符 ( ** >> **)。  
  
 有关序列化示例，请参阅文章[序列化︰ 将对象序列化为](../../mfc/serialization-serializing-an-object.md)。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)可以列出`CAge`中所有使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample #&13;](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)




