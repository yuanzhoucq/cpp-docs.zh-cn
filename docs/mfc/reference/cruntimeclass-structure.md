---
title: CRuntimeClass 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84597f8d728b0781231cc07b84ad91495b870437
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852074"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass 结构
每个类派生自`CObject`与关联`CRuntimeClass`结构，它可用于获取有关对象或其基本类在运行时的信息。  
  
## <a name="syntax"></a>语法  
  
```  
struct CRuntimeClass  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRuntimeClass::CreateObject](#createobject)|在运行时创建的对象。|  
|[CRuntimeClass::FromName](#fromname)|在运行时使用熟悉的类名期间创建的对象。|  
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|确定是否从指定的类派生的类。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|类的名称。|  
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|对象大小（以字节为单位）。|  
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|一个指向`CRuntimeClass`结构的基类。|  
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|指向动态创建对象的函数的指针。|  
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|返回`CRuntimeClass`结构 （仅可用时动态链接）。|  
|[CRuntimeClass::m_wSchema](#m_wschema)|类的架构数字。|  
  
## <a name="remarks"></a>备注  
 `CRuntimeClass` 是一种结构，因此不会将一个基类。  
  
 当需要额外的类型检查函数自变量时，或者必须编写特殊用途的代码基于对象的类时，在运行时确定对象的类的功能非常有用。 C++ 语言不直接支持运行时类信息。  
  
 `CRuntimeClass` 提供有关相关的 c + + 对象，例如指向指针的信息`CRuntimeClass`的基本类和相关类的 ASCII 类名称。 此结构还实现了可用于动态创建对象，指定通过使用熟悉的名称，并确定是否相关的类派生自特定类的对象的类型的各种函数。  
  
 有关使用的详细信息`CRuntimeClass`，请参阅文章[访问运行时类信息](../../mfc/accessing-run-time-class-information.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CRuntimeClass`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="createobject"></a>  CRuntimeClass::CreateObject  
 调用此函数可在运行时动态创建指定的类。  
  
```  
CObject* CreateObject();  
  
static CObject* PASCAL CreateObject(LPCSTR lpszClassName);  
  
static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```  
  
### <a name="parameters"></a>参数  
 *lpszClassName*  
 要创建的类的熟悉的名称。  
  
### <a name="return-value"></a>返回值  
 一个指向新创建的对象或如果找不到类名称，或者没有足够的内存来创建对象，则为 NULL。  
  
### <a name="remarks"></a>备注  
 类派生自`CObject`可以支持动态创建，这是在运行时创建指定类的对象的功能。 文档、 视图和框架类，例如，应支持动态创建。 有关详细信息动态创建并`CreateObject`成员，请参阅[CObject 类](../../mfc/using-cobject.md)并[CObject 类： 指定级别的功能](../../mfc/specifying-levels-of-functionality.md)。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="fromname"></a>  CRuntimeClass::FromName  
 调用此函数可检索`CRuntimeClass`与熟悉的名称关联的结构。  
  
```  
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);  
  
static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```  
  
### <a name="parameters"></a>参数  
 *lpszClassName*  
 熟悉的名称的类派生自`CObject`。  
  
### <a name="return-value"></a>返回值  
 一个指向`CRuntimeClass`对象，如传入与名称对应*lpszClassName*。 如果不找到任何匹配的类名称，该函数将返回 NULL。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]  
  
##  <a name="isderivedfrom"></a>  CRuntimeClass::IsDerivedFrom  
 调用此函数可确定调用类派生类中指定*pBaseClass*参数。  
  
```  
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;

 
```  
  
### <a name="parameters"></a>参数  
 *pBaseClass*  
 熟悉的名称的类派生自`CObject`。  
  
### <a name="return-value"></a>返回值  
 如果类调用`IsDerivedFrom`派生自基本类，其`CRuntimeClass`结构是给定作为参数; 否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 "浏览"从链的派生类的成员的类到顶部取决于此关系。 如果未找到匹配的类的基类，此函数仅返回 FALSE。  
  
> [!NOTE]
>  若要使用`CRuntimeClass`结构，您必须在你想要检索的运行时对象信息的类的实现包括 IMPLEMENT_DYNAMIC、 IMPLEMENT_DYNCREATE 或 IMPLEMENT_SERIAL 宏。  
  
 有关使用的详细信息`CRuntimeClass`，请参阅文章[CObject 类： 访问运行时类信息](../../mfc/accessing-run-time-class-information.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]  
  
##  <a name="m_lpszclassname"></a>  CRuntimeClass::m_lpszClassName  
 以 null 结尾的字符串，包含 ASCII 类名。  
  
### <a name="remarks"></a>备注  
 此名称可用于创建的类实例`FromName`成员函数。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="m_nobjectsize"></a>  CRuntimeClass::m_nObjectSize  
 对象，以字节为单位的大小。  
  
### <a name="remarks"></a>备注  
 如果对象具有数据成员指向已分配的内存的则不包含该内存的大小。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="m_pbaseclass"></a>  CRuntimeClass::m_pBaseClass  
 如果你的应用程序静态链接到 MFC，此数据成员包含一个指向`CRuntimeClass`结构的基类。  
  
### <a name="remarks"></a>备注  
 如果你的应用程序动态链接到 MFC 库，请参阅[m_pfnGetBaseClass](#m_pfngetbaseclass)。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="m_pfncreateobject"></a>  CRuntimeClass::m_pfnCreateObject  
 指向将创建您的类的对象的默认构造函数的函数指针。  
  
### <a name="remarks"></a>备注  
 此指针才有效的类支持动态创建;否则，该函数返回 NULL。  
  
##  <a name="m_pfngetbaseclass"></a>  CRuntimeClass::m_pfnGetBaseClass  
 如果你的应用程序使用 MFC 库作为共享 DLL，此数据成员将指向返回的函数`CRuntimeClass`结构的基类。  
  
### <a name="remarks"></a>备注  
 如果你的应用程序静态链接到 MFC 库，请参阅[m_pBaseClass](#m_pbaseclass)。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[IsDerivedFrom](#isderivedfrom)。  
  
##  <a name="m_wschema"></a>  CRuntimeClass::m_wSchema  
 架构数字 (-1 的不可序列化类)。  
  
### <a name="remarks"></a>备注  
 对架构数字的详细信息，请参阅[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)宏。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[IsDerivedFrom](#isderivedfrom)。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)   
 [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)   
 [RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)   
 [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)   
 [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)   
 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)



