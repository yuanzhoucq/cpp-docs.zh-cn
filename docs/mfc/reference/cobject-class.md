---
title: "CObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c0384392d42196e4365c59670537819435ce1e45
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[CObject::IsKindOf](#iskindof)|测试到给定类的此对象的关系。|  
|[CObject::IsSerializable](#isserializable)|若要查看此对象是否可以序列化的测试。|  
|[Cobject:: Serialize](#serialize)|加载或存储从/到存档的对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CObject::operator 删除](#operator_delete)|特殊**删除**运算符。|  
|[新的 CObject::operator](#operator_new)|特殊**新**运算符。|  
  
## <a name="remarks"></a>备注  
 它可用作不仅库类的根如`CFile`和`CObList`，而且对于你编写的类。 `CObject`提供基本的服务，包括  
  
-   序列化支持  
  
-   运行时类信息  
  
-   对象诊断输出  
  
-   集合类与兼容性  
  
 请注意，`CObject`不支持多重继承。 派生的类只能有一个`CObject`基类，并且`CObject`必须位于层次结构中最左侧。 它是允许的但是，有的结构和非- `CObject`-派生右侧多重继承分支中的类。  
  
 将实现从的主要优点`CObject`派生，如果你使用某些类实现和声明中的可选宏。  
  
 第一级宏， [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)和[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)，允许运行时访问的类名称和在层次结构中的位置。 这样，反过来，有意义的诊断转储。  
  
 第二级别宏， [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)，包括第一级宏的所有功能，并且它们使对象可以"序列化"与"存档"。  
  
 有关一般派生 Microsoft 基础类和 c + + 类和使用信息`CObject`，请参阅[使用 CObject](../../mfc/using-cobject.md)和[序列化](../../mfc/serialization-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CObject`  
  
## <a name="requirements"></a>惠?  
 **标头：** afx.h  
  
##  <a name="assertvalid"></a>CObject::AssertValid  
 验证此对象的完整性。  
  
```  
virtual void AssertValid() const;  
```  
  
### <a name="remarks"></a>备注  
 `AssertValid`通过检查其内部状态执行有效性检查对此对象。 为库的调试版本中`AssertValid`可能断言并因此终止此程序包含在一条消息，列出的行号和文件名断言失败。  
  
 当你编写您自己的类时，则应重写`AssertValid`函数以提供为你自己以及你的类的其他用户的诊断服务。 重写`AssertValid`通常调用`AssertValid`再进行检查数据成员唯一派生的类的其基本类的函数。  
  
 因为`AssertValid`是**const**函数，你不允许在测试期间更改对象状态。 派生的类`AssertValid`函数不应引发异常但而是应断言它们是否检测到无效对象数据。  
  
 定义"有效期"取决于对象的类。 作为一条规则，该函数应执行"浅表检查"。 也就是说，如果对象包含对其他对象的指针，它应检查以查看是否指针不为 null，但它不应执行测试指针所引用的对象上的有效性。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`中所有使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]  
  
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
 由派生类的构造函数自动调用默认版本。  
  
 如果你的类是可序列化 (它融合了`IMPLEMENT_SERIAL`宏)，则必须在类声明具有默认构造函数 （不带任何参数的构造函数）。 如果不需要默认构造函数，声明一个私有或受保护的"空"的构造函数。 有关详细信息，请参阅[使用 CObject](../../mfc/using-cobject.md)。  
  
 标准 c + + 默认类复制构造函数执行逐个成员复制。 私钥是否存在`CObject`复制构造函数可保证编译器错误消息，如果你的类的复制构造函数是所需但不可用。 如果你的类需要此功能，因此必须提供复制构造函数。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`中使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]  
  
##  <a name="dump"></a>CObject::Dump  
 转储到对象的内容[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象。  
  
```  
virtual void Dump(CDumpContext& dc) const;  
```  
  
### <a name="parameters"></a>参数  
 `dc`  
 转储，通常的诊断转储上下文`afxDump`。  
  
### <a name="remarks"></a>备注  
 当你编写您自己的类时，则应重写`Dump`函数以提供为你自己以及你的类的其他用户的诊断服务。 重写`Dump`通常调用`Dump`之前打印数据成员唯一派生的类的其基本类的函数。 `CObject::Dump`打印类名称，如果你的类使用`IMPLEMENT_DYNAMIC`或`IMPLEMENT_SERIAL`宏。  
  
> [!NOTE]
>  你`Dump`函数应不会打印出来其输出的末尾处的换行字符。  
  
 `Dump`调用仅在 Microsoft 基础类库的调试版本中有意义。 调用、 函数声明和使用的函数实现应尖括号**#ifdef _DEBUG** /  `#endif`条件编译的语句。  
  
 由于`Dump`是**const**函数，你不允许在转储过程中更改对象状态。  
  
 [CDumpContext 插入 (<<) 运算符](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt)调用`Dump`时`CObject`插入指针。  
  
 `Dump`允许仅"非循环"转储的对象。 例如，你可以转储对象列表，但如果其中一个对象是本身的列表，将最终溢出堆栈。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`中所有使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]  
  
##  <a name="getruntimeclass"></a>CObject::GetRuntimeClass  
 返回`CRuntimeClass`结构对应于此对象的类。  
  
```  
virtual CRuntimeClass* GetRuntimeClass() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构对应于此对象的类; 永远不会**NULL**。  
  
### <a name="remarks"></a>备注  
 还有一个`CRuntimeClass`每个结构`CObject`-派生类。 结构成员如下所示：  
  
- **LPCSTR m_lpszClassName**包含 ASCII 类名的以 null 结尾的字符串。  
  
- **int m_nObjectSize**对象，以字节为单位的大小。 如果该对象具有数据成员的指向分配的内存，则该内存的大小不包括。  
  
- **UINT m_wSchema**架构数字 (-1 表示不可序列化类)。 请参阅[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏有关的架构数字的说明。  
  
- **CObject\* (PASCAL\* m_pfnCreateObject) （)**创建你的类的对象的默认构造函数的函数指针 (有效前提的类支持动态创建; 否则，返回**NULL**).  
  
- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) （)**如果你的应用程序动态链接到 MFC 的 AFXDLL 版本中，指向函数的返回`CRuntimeClass`基本类的结构。  
  
- **CRuntimeClass\* m_pBaseClass**如果你的应用程序静态链接到 MFC，指向的指针`CRuntimeClass`基本类的结构。  
  
 此函数需要使用[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)， [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)，或[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)类实现中的宏。 否则，你将获得不正确的结果。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`中所有使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]  
  
##  <a name="iskindof"></a>CObject::IsKindOf  
 测试到给定类的此对象的关系。  
  
```  
BOOL IsKindOf(const CRuntimeClass* pClass) const;  
```  
  
### <a name="parameters"></a>参数  
 `pClass`  
 指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构与你`CObject`-派生类。  
  
### <a name="return-value"></a>返回值  
 如果对象都对应于类; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数将测试`pClass`以查看是否 （1） 它是指定类的对象或 （2） 它是从指定的类派生的类的对象。 此函数仅适用于使用声明的类[DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic)， [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)，或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏。  
  
 不要使用此功能进行了广泛因为它使您无法获得 c + + 多态性功能。 改为使用虚函数。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`中所有使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]  
  
##  <a name="isserializable"></a>CObject::IsSerializable  
 测试此对象是否是适合序列化。  
  
```  
BOOL IsSerializable() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果此对象可以序列化; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 必须是可序列化的类，包含其声明[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏和实现必须包含[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。  
  
> [!NOTE]
>  不会覆盖此函数。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`中所有使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]  
  
##  <a name="operator_delete"></a>CObject::operator 删除  
 发行版的库中，运算符**删除**释放运算符分配的内存**新**。  
  
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
  
 如果你使用的代码行  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 在您的实现中的任何前。CPP 文件，然后第三个版本的**删除**将使用，以便日后制作报表分配的块中存储的文件名和行号。 无需担心提供额外的参数;宏负责为你的程序。  
  
 即使不使用`DEBUG_NEW`处于调试模式，您仍然收到泄漏检测，但没有源代码文件行号 reporting 上面所述。  
  
 如果重写运算符**新**和**删除**，丧失此诊断功能。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`中使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]  
  
##  <a name="operator_new"></a>新的 CObject::operator  
 发行版的库中，运算符**新**执行相似的方式实现最佳的内存分配`malloc`。  
  
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
  
 如果你使用的代码行  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 在您的实现中的任何前。CPP 文件然后第二个版本**新**将使用，以便日后制作报表分配的块中存储的文件名和行号。 无需担心提供额外的参数;宏负责为你的程序。  
  
 即使不使用`DEBUG_NEW`处于调试模式，您仍然收到泄漏检测，但没有源代码文件行号 reporting 上面所述。  
  
> [!NOTE]
>  如果你重写此运算符，还必须重写**删除**。 不使用标准库**_new_handler**函数。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`中使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]  
  
##  <a name="serialize"></a>Cobject:: Serialize  
 从存档读取该对象或将该对象写入存档。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 `ar`  
 A`CArchive`要序列化或从对象。  
  
### <a name="remarks"></a>备注  
 必须重写`Serialize`为每个你想要序列化的类。 重写`Serialize`必须首先调用`Serialize`其基本类的函数。  
  
 你还必须使用[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏在类声明中，并且你必须使用[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏的实现中。  
  
 使用[CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading)或[CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring)来确定存档是否已加载或存储。  
  
 `Serialize`由调用[CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject)和[CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject)。 这些函数与之关联`CArchive`插入运算符 (  **< \<** ) 和提取运算符 (  **>>** )。  
  
 有关序列化示例，请参阅文章[序列化： 将对象序列化为](../../mfc/serialization-serializing-an-object.md)。  
  
### <a name="example"></a>示例  
 请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)有关的列表`CAge`中所有使用类`CObject`示例。  
  
 [!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)



