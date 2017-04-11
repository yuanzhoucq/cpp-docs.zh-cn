---
title: "CComCoClass 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
dev_langs:
- C++
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
caps.latest.revision: 19
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 967c919bb68890c51be6a0800db90692346e2b7d
ms.lasthandoff: 03/31/2017

---
# <a name="ccomcoclass-class"></a>CComCoClass 类
此类提供方法以创建类的实例，并获取其属性。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, const CLSID* pclsid = &CLSID_NULL>  
class CComCoClass
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`CComCoClass`。  
  
 *pclsid*  
 指向对象的 CLSID 的指针。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComCoClass::CreateInstance](#createinstance)|（静态）创建类和接口的查询的实例。|  
|[CComCoClass::Error](#error)|（静态）返回到客户端丰富的错误信息。|  
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|（静态）返回对象的类标识符。|  
|[CComCoClass::GetObjectDescription](#getobjectdescription)|（静态）重写以返回对象的说明。|  
  
## <a name="remarks"></a>备注  
 `CComCoClass`提供用于检索对象的 CLSID、 设置错误的信息，以及创建类的实例方法。 在中的任何类注册[对象映射](http://msdn.microsoft.com/en-us/b57619cc-534f-4b8f-bfd4-0c12f937202f)应派生自`CComCoClass`。  
  
 `CComCoClass`此外定义了你的对象的默认类工厂和聚合模型。 `CComCoClass`使用以下两个宏︰  
  
- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)声明类工厂为[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)。  
  
- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)声明你的对象可以进行聚合。  
  
 你可以通过在类定义中指定的另一个宏覆盖这些默认值之一。 例如，若要使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)而不是`CComClassFactory`，指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)宏︰  
  
 [!code-cpp[NVC_ATL_COM #2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="createinstance"></a>CComCoClass::CreateInstance  
 使用这些`CreateInstance`函数来创建实例的 COM 对象并检索的接口指针，而不使用 COM API。  
  
```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```  
  
### <a name="parameters"></a>参数  
 `Q`  
 应返回通过 COM 接口`pp`。  
  
 *punkOuter*  
 [in]未知的外部对象或聚合的控制未知。  
  
 `pp`  
 [out]如果创建成功接收的请求的接口指针的指针变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。 请参阅[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关可能的返回值的说明。  
  
### <a name="remarks"></a>备注  
 典型对象创建; 请使用此函数的第一个重载当你需要将聚合正在创建的对象时，请使用第二个重载。  
  
 实现所需的 COM 对象的 ATL 类 (即，使用作为第一个模板参数的类[CComCoClass](../../atl/reference/ccomcoclass-class.md)) 必须在与调用的代码相同的项目。 创建 COM 对象由类工厂注册此 ATL 类执行。  
  
 这些函数可用于创建已阻止从正在使用的外部创建的对象[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)宏。 它们也是在你想要避免效率的原因而 COM API 的情况下有用的。  
  
 请注意，接口`Q`必须具有与之关联的、 可以使用检索 IID [__uuidof](../../cpp/uuidof-operator.md)运算符。  
  
### <a name="example"></a>示例  
 在下面的示例中，`CDocument`向导生成的 ATL 类派生自`CComCoClass`实现**IDocument**接口。 在对象映射中注册类`OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO`宏，因此客户端不能创建的文档使用实例[CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615)。 `CApplication`是提供一种方法在它自己的 COM 接口来创建文档类的实例之一的组件类。 下面的代码显示如何轻松它创建的文档类使用实例`CreateInstance`成员继承自`CComCoClass`基类。  
  
 [!code-cpp[NVC_ATL_COM #11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]  
  
##  <a name="error"></a>CComCoClass::Error  
 此静态函数将设置`IErrorInfo`接口，以向客户端提供错误信息。  
  
```
static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance ());

static HRESULT Error(
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```  
  
### <a name="parameters"></a>参数  
 `lpszDesc`  
 [in]描述错误的字符串。 Unicode 版的`Error`指定`lpszDesc`属于类型**LPCOLESTR**; ANSI 版本指定一种`LPCSTR`。  
  
 `iid`  
 [in]定义错误的接口的 IID 或`GUID_NULL`（默认值） 如果错误由操作系统定义的。  
  
 `hRes`  
 [in]`HRESULT`要返回到调用方。 默认值为 0。 有关详细信息`hRes`，请参阅备注。  
  
 `nID`  
 [in]存储的错误描述字符串资源标识符。 此值应介于 0x0200 和 0xFFFF，之间 （含）。 在调试版本中，**断言**时将导致`nID`没有有效的字符串进行索引。 在发布版本中的错误描述字符串将设置为"未知错误。"  
  
 `dwHelpID`  
 [in]错误帮助上下文标识符。  
  
 `lpszHelpFile`  
 [in]路径和名称的描述错误的帮助文件。  
  
 `hInst`  
 [in]资源句柄。 默认情况下，此参数是**_AtlModule::GetResourceInstance**，其中**_AtlModule**是全局实例[CAtlModule](../../atl/reference/catlmodule-class.md)。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 若要调用`Error`，你的对象必须实现`ISupportErrorInfo Interface`接口。  
  
 如果`hRes`参数不为零，然后`Error`返回的值`hRes`。 如果`hRes`为零，则的前四个版本`Error`返回`DISP_E_EXCEPTION`。 最后两个版本都会返回的结果宏**MAKE_HRESULT (1，FACILITY_ITF，** `nID` **)**。  
  
##  <a name="getobjectclsid"></a>CComCoClass::GetObjectCLSID  
 提供检索对象的 CLSID 的一致方法。  
  
```
static const CLSID& WINAPI GetObjectCLSID();
```  
  
### <a name="return-value"></a>返回值  
 对象的类标识符。  
  
##  <a name="getobjectdescription"></a>CComCoClass::GetObjectDescription  
 此静态函数将检索你的类对象的文本说明。  
  
```
static LPCTSTR WINAPI GetObjectDescription();
```  
  
### <a name="return-value"></a>返回值  
 类对象的说明。  
  
### <a name="remarks"></a>备注  
 默认实现返回**NULL**。 你可以使用重写此方法[DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description)宏。 例如:   
  
 [!code-cpp[NVC_ATL_COM #12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]  
  
 `GetObjectDescription`由调用**IComponentRegistrar::GetComponents**。 **IComponentRegistrar**是自动化接口，您可以注册和取消注册在 DLL 中的各个组件。 当使用 ATL 项目向导创建的组件注册机构对象时，向导将自动执行**IComponentRegistrar**接口。 **IComponentRegistrar**通常由 Microsoft Transaction Server。  
  
 有关 ATL 项目向导的详细信息，请参阅文章[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

