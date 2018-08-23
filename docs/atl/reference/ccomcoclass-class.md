---
title: CComCoClass 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6043277eff17340cd57d0a6ee1bb8e84625f45b9
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42571750"
---
# <a name="ccomcoclass-class"></a>CComCoClass 类
此类提供用于创建类的实例并获取其属性的方法。  
  
## <a name="syntax"></a>语法  
  
```
template <class T, const CLSID* pclsid = &CLSID_NULL>  
class CComCoClass
```  
  
#### <a name="parameters"></a>参数  
 *T*  
 您的类，派生自`CComCoClass`。  
  
 *pclsid*  
 指向对象的 CLSID 的指针。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CComCoClass::CreateInstance](#createinstance)|（静态）创建类和接口的查询的实例。|  
|[CComCoClass::Error](#error)|（静态）返回到客户端的丰富的错误信息。|  
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|（静态）返回对象的类标识符。|  
|[CComCoClass::GetObjectDescription](#getobjectdescription)|（静态）重写以返回对象的说明。|  
  
## <a name="remarks"></a>备注  
 `CComCoClass` 提供用于检索对象的 CLSID 以及设置错误的信息，创建类的实例方法。 任何类中注册[对象映射](http://msdn.microsoft.com/b57619cc-534f-4b8f-bfd4-0c12f937202f)应派生自`CComCoClass`。  
  
 `CComCoClass` 此外定义了您的对象的默认类工厂和聚合模型。 `CComCoClass` 使用以下两个宏：  
  
- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)声明为类工厂[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)。  
  
- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)声明您的对象可以进行聚合。  
  
 可以通过在类定义中指定的另一个宏来覆盖这些默认值之一。 例如，若要使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)而不是`CComClassFactory`，指定[DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2)宏：  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="createinstance"></a>  CComCoClass::CreateInstance  
 使用这些`CreateInstance`函数来创建实例的 COM 对象，并检索接口指针，而不使用 COM API。  
  
```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```  
  
### <a name="parameters"></a>参数  
 *Q*  
 应通过返回的 COM 接口*pp*。  
  
 *punkOuter*  
 [in]未知的外部或聚合的控制未知。  
  
 *pp*  
 [out]如果创建成功接收的请求的接口指针的指针变量的地址。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT 值。 请参阅[CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)有关可能的返回值的说明 Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 此函数的第一个重载用于典型对象创建;当您需要聚合正在创建的对象时，请使用第二个重载。  
  
 实现所需的 COM 对象的 ATL 类 (即，使用作为第一个模板参数的类[CComCoClass](../../atl/reference/ccomcoclass-class.md)) 必须在与调用代码相同的项目。 为此 ATL 类注册类工厂执行 COM 对象的创建。  
  
 这些函数可用于创建已阻止从正在使用的外部创建对象的对象[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto)宏。 它们也是在你想要避免效率的原因 COM API 的情况下很有用。  
  
 请注意，该接口*Q*必须具有与之关联，可以使用检索的 IID [__uuidof](../../cpp/uuidof-operator.md)运算符。  
  
### <a name="example"></a>示例  
 在以下示例中，`CDocument`向导生成的 ATL 类派生自`CComCoClass`实现`IDocument`接口。 因此，客户端不能创建实例文档使用的类与 OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO 宏在对象映射中注册[CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)。 `CApplication` 是一个其自己的 COM 接口，用于创建文档类的实例提供一种方法是组件类。 下面的代码显示如何轻松创建文档类使用的实例`CreateInstance`成员继承自`CComCoClass`基类。  
  
 [!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]  
  
##  <a name="error"></a>  CComCoClass::Error  
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
 *lpszDesc*  
 [in]描述错误的字符串。 Unicode 版本`Error`规定*lpszDesc*属于类型 LPCOLESTR; ANSI 版本指定的类型 LPCSTR。  
 *iid*  
 [in]如果错误由操作系统定义的错误或 GUID_NULL （默认值） 的接口的 IID。  
  
 *hRes*  
 [in]所需的 HRESULT 返回到调用方。 默认值为 0。 有关详细信息*hRes*，请参阅备注。  
  
 *nID*  
 [in]资源标识符的错误描述字符串的存储位置。 此值应介于 0x0200 和 0xffff 内，之间 （含）。 在调试版本中， **ASSERT**如果会导致*nID*没有有效的字符串进行索引。 在发布版本中的错误描述字符串将设置为"未知错误。"  
  
 *dwHelpID*  
 [in]错误的帮助上下文标识符。  
  
 *lpszHelpFile*  
 [in]路径和描述错误的帮助文件的名称。  
  
 *hInst*  
 [in]资源的句柄。 默认情况下，此参数是`_AtlModule::GetResourceInstance`，其中`_AtlModule`是全局实例[CAtlModule](../../atl/reference/catlmodule-class.md)。  
  
### <a name="return-value"></a>返回值  
 标准的 HRESULT 值。 有关详细信息，请参阅“备注”。  
  
### <a name="remarks"></a>备注  
 若要调用`Error`，您的对象必须实现`ISupportErrorInfo Interface`接口。  
  
 如果*hRes*参数为非零值，然后`Error`返回的值*hRes*。 如果*hRes*为零，则前四个版本的`Error`返回 DISP_E_EXCEPTION。 最后两个版本都会返回结果的宏**MAKE_HRESULT (1，FACILITY_ITF，** *nID* **)**。  
  
##  <a name="getobjectclsid"></a>  CComCoClass::GetObjectCLSID  
 提供了一致地检索对象的 CLSID。  
  
```
static const CLSID& WINAPI GetObjectCLSID();
```  
  
### <a name="return-value"></a>返回值  
 对象的类标识符。  
  
##  <a name="getobjectdescription"></a>  CComCoClass::GetObjectDescription  
 此静态函数检索您的类对象的文本说明。  
  
```
static LPCTSTR WINAPI GetObjectDescription();
```  
  
### <a name="return-value"></a>返回值  
 类对象的说明。  
  
### <a name="remarks"></a>备注  
 默认实现返回 NULL。 可以重写此方法替换[DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description)宏。 例如：  
  
 [!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]  
  
 `GetObjectDescription` 由调用`IComponentRegistrar::GetComponents`。 `IComponentRegistrar` 是，可注册和注销 DLL 中的各个组件的自动化接口。 当使用 ATL 项目向导创建的支持组件注册对象时，该向导将自动执行`IComponentRegistrar`接口。 `IComponentRegistrar` 通常使用 Microsoft Transaction Server。  
  
 ATL 项目向导的详细信息，请参阅文章[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
