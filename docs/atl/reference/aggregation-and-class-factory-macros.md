---
title: "聚合和类工厂宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
caps.latest.revision: 17
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 4509f7be36e45cf96a938e30ec0f82ec0c9836b5
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="aggregation-and-class-factory-macros"></a>聚合和类工厂宏
这些宏提供控制聚合的并声明类工厂的方法。  
  
|||  
|-|-|  
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|声明您的对象可以是聚合 （默认值）。|  
|[DECLARE_CLASSFACTORY](#declare_classfactory)|声明类工厂为[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，ATL 默认类工厂。|  
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|声明类工厂对象是类工厂。|  
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|声明[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)要类工厂。|  
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|声明[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)要类工厂。|  
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|声明[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)要类工厂。|  
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|声明了一个虚拟`GetControllingUnknown`函数。|  
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|声明您的对象不能进行聚合。|  
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|声明您的对象必须进行聚合。|  
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|检查未知的外部对象的值，并声明您的对象可聚合或不可聚合时，视情况而定。|  
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|内部对象的构造期间删除可防止外部对象。|  
|[DECLARE_VIEW_STATUS](#declare_view_status)|指定**VIEWSTATUS**到容器的标志。|  

## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
   
##  <a name="declare_aggregatable"></a>DECLARE_AGGREGATABLE  
 指定可聚合对象。  
  
```
DECLARE_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]您定义为聚合类的名称。  
  
### <a name="remarks"></a>备注  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含此宏来指定默认聚合模型。 若要重写此默认值，指定[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)或[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)在类定义的宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&121;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="declare_classfactory"></a>DECLARE_CLASSFACTORY  
 声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)要类工厂。  
  
```
DECLARE_CLASSFACTORY()
```  
  
### <a name="remarks"></a>备注  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md)使用此宏来声明您的对象的默认类工厂。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#55;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]  
  
##  <a name="ccomclassfactory_class"></a>CComClassFactory 类  
 此类实现[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)接口。  
  
```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>备注  
 `CComClassFactory`实现[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)接口，它包含用于创建特定的 CLSID，一个对象，以及锁定在内存中允许更快地创建新对象的类工厂的方法。 **IClassFactory**必须为您注册系统注册表中以及为你分配 CLSID 的每个类实现。  
  
 ATL 对象通常通过派生自获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)，其中声明`CComClassFactory`作为默认类工厂。 若要重写此默认值，指定一个`DECLARE_CLASSFACTORY` *XXX*在类定义的宏。 例如， [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)宏的类工厂使用指定的类︰  
  
 [!code-cpp[NVC_ATL_COM&#8;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
 上面的类定义指定**CMyClassFactory**将用作该对象的默认类工厂。 **CMyClassFactory**必须派生自`CComClassFactory`并重写`CreateInstance`。  
  
 ATL 提供三个其他声明类工厂的宏︰  
  
- [DECLARE_CLASSFACTORY2](#declare_classfactory2)使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，哪些控件创建到一个许可证。  
  
- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，从而在多个单元中创建对象。  
  
- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)使用[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，它会构造一个[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象。  
  
##  <a name="declare_classfactory_ex"></a>DECLARE_CLASSFACTORY_EX  
 声明`cf`要类工厂。  
  
```
DECLARE_CLASSFACTORY_EX( cf )
```  
  
### <a name="parameters"></a>参数  
 `cf`  
 [in]实现您的类工厂对象的类的名称。  
  
### <a name="remarks"></a>备注  
 `cf`参数必须派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)并重写`CreateInstance`方法。  
  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏，它指定`CComClassFactory`作为默认类工厂。 但是，通过包括`DECLARE_CLASSFACTORY_EX`宏在您的对象类定义中，重写此默认值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#8;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]  
  
##  <a name="declare_classfactory2"></a>DECLARE_CLASSFACTORY2  
 声明[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)要类工厂。  
  
```
DECLARE_CLASSFACTORY2( lic )
```  
  
### <a name="parameters"></a>参数  
 *许可证*  
 [in]一个实现类`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。  
  
### <a name="remarks"></a>备注  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏，它指定[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 但是，通过包括`DECLARE_CLASSFACTORY2`宏在您的对象类定义中，重写此默认值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#2;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
##  <a name="ccomclassfactory2_class"></a>CComClassFactory2 类  
 此类实现[IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720)接口。  
  
```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```    
  
### <a name="parameters"></a>参数  
 *许可证*  
 实现以下静态函数的类︰  
  
- **静态 BOOL VerifyLicenseKey (BSTR** `bstr` **);**  
  
- **静态 BOOL GetLicenseKey (DWORD** `dwReserved` **，BSTR\* ** `pBstr` **);**  
  
- **静态 BOOL IsLicenseValid （);**  
  
### <a name="remarks"></a>备注  
 `CComClassFactory2`实现[IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720)接口，这是一个扩展的[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)。 **IClassFactory2**控件对象创建到一个许可证。 类工厂执行一个授权的计算机上可以提供一个运行时许可证密钥。 此许可密钥允许应用程序时要实例化对象的完整的计算机许可证不存在。  
  
 ATL 对象通常通过派生自获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)，其中声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 若要使用`CComClassFactory2`，指定[DECLARE_CLASSFACTORY2](#declare_classfactory2)对象的类定义中的宏。 例如:   
  
 [!code-cpp[NVC_ATL_COM&#2;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]  
  
 **CMyLicense**的模板参数`CComClassFactory2`，必须实现的静态函数`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。 下面是简单许可证类的示例︰  
  
 [!code-cpp[NVC_ATL_COM&#3;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]  
  
 `CComClassFactory2`派生自两**CComClassFactory2Base**和*许可证*。 **CComClassFactory2Base**，反过来，派生自**IClassFactory2**和**CComObjectRootEx\< CComGlobalsThreadModel&1;>**。  
  
##  <a name="declare_classfactory_auto_thread"></a>DECLARE_CLASSFACTORY_AUTO_THREAD  
 声明[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)要类工厂。  
  
```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```  
  
### <a name="remarks"></a>备注  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏，它指定[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 但是，通过包括`DECLARE_CLASSFACTORY_AUTO_THREAD`宏在您的对象类定义中，重写此默认值。  
  
 在多个单元 （在进程外的服务器中） 中创建对象时，添加`DECLARE_CLASSFACTORY_AUTO_THREAD`到您的类。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#9;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="ccomclassfactoryautothread_class"></a>CComClassFactoryAutoThread 类  
 此类实现[IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)接口，并允许在多个单元中创建的对象。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```  
  
### <a name="remarks"></a>备注  
 `CComClassFactoryAutoThread`类似于[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但允许在多个单元中创建的对象。 若要充分利用这种支持，派生出您 EXE 模块从[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。  
  
 ATL 对象通常通过派生自获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)，其中声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 若要使用`CComClassFactoryAutoThread`，指定[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)对象的类定义中的宏。 例如:   
  
 [!code-cpp[NVC_ATL_COM&#9;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]  
  
##  <a name="declare_classfactory_singleton"></a>DECLARE_CLASSFACTORY_SINGLETON  
 声明[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)要类工厂。  
  
```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```  
  
### <a name="parameters"></a>参数  
 `obj`  
 [in]类对象的名称。  
  
### <a name="remarks"></a>备注  
 [CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏，它指定[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 但是，通过包括`DECLARE_CLASSFACTORY_SINGLETON`宏在您的对象类定义中，重写此默认值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#10;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="ccomclassfactorysingleton_class"></a>CComClassFactorySingleton 类  
 此类派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)来构造一个对象。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```  
  
### <a name="parameters"></a>参数  
 `T`  
 您的类。  
  
 `CComClassFactorySingleton`派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)来构造一个对象。 每次调用`CreateInstance`方法只需查询此对象的接口指针。  
  
### <a name="remarks"></a>备注  
 ATL 对象通常通过派生自获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)，其中声明`CComClassFactory`作为默认类工厂。 若要使用`CComClassFactorySingleton`，指定[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)对象的类定义中的宏。 例如:   
  
 [!code-cpp[NVC_ATL_COM&#10;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]  
  
##  <a name="declare_get_controlling_unknown"></a>DECLARE_GET_CONTROLLING_UNKNOWN  
 声明的虚函数`GetControllingUnknown`。  
  
```
DECLARE_GET_CONTROLLING_UNKNOWN()
```  
  
### <a name="remarks"></a>备注  
 如果您将看到编译器错误消息，将此宏添加到您的对象`GetControllingUnknown`是不确定的 (例如，在**CComAggregateCreator**)。  
  
##  <a name="declare_not_aggregatable"></a>DECLARE_NOT_AGGREGATABLE  
 指定您的对象不能进行聚合。  
  
```
DECLARE_NOT_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]您定义为不可聚合的类对象的名称。  
  
### <a name="remarks"></a>备注  
 `DECLARE_NOT_AGGREGATABLE`导致`CreateInstance`返回错误 ( **CLASS_E_NOAGGREGATION**) 如果试图对其进行聚合到您的对象。  
  
 默认情况下， [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)宏，它指定可聚合对象。 若要重写此默认行为，包括`DECLARE_NOT_AGGREGATABLE`类定义中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&121;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]  
  
##  <a name="declare_only_aggregatable"></a>DECLARE_ONLY_AGGREGATABLE  
 指定您的对象必须可聚合。  
  
```
DECLARE_ONLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]您定义为仅可聚合的类对象的名称。  
  
### <a name="remarks"></a>备注  
 `DECLARE_ONLY_AGGREGATABLE`将导致错误 ( **E_FAIL**) 如果尝试向**CoCreate**您作为非聚合对象的对象。  
  
 默认情况下， [CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)宏，它指定可聚合对象。 若要重写此默认行为，包括`DECLARE_ONLY_AGGREGATABLE`类定义中。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&125;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]  
  
##  <a name="declare_poly_aggregatable"></a>DECLARE_POLY_AGGREGATABLE  
 指定的实例**CComPolyObject \< ** *x* ** > **创建您的对象时创建。  
  
```
DECLARE_POLY_AGGREGATABLE( x )
```  
  
### <a name="parameters"></a>参数  
 *x*  
 [in]您定义为聚合或不可聚合的类对象的名称。  
  
### <a name="remarks"></a>备注  
 在创建过程中，将检查未知的外部对象的值。 如果它是**NULL**， **IUnknown**对于非聚合对象的实现。 如果不是未知的外部对象**NULL**， **IUnknown**聚合对象实现。  
  
 使用的优点`DECLARE_POLY_AGGREGATABLE`是避免同时`CComAggObject`和`CComObject`模块来处理聚合的和非聚合情况中。 单个`CComPolyObject`对象处理这两种情况。 这意味着只有一份 vtable 和函数的一个副本存在于您的模块。 如果您 vtable 很大，这可以显著减少模块大小。 但是，如果您 vtable 很小，则使用`CComPolyObject`可能会导致稍大一些的模块的大小，因为它不优化聚合或非聚合对象，允许进行`CComAggObject`和`CComObject`。  
  
 `DECLARE_POLY_AGGREGATABLE`宏自动声明对象中，如果您使用 ATL 控件向导创建完全控制。  
  
##  <a name="declare_protect_final_construct"></a>DECLARE_PROTECT_FINAL_CONSTRUCT  

 防止您的对象如果被删除 (期间[FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) 内部聚合的对象递增则引用计数会递减为 0 的计数。  
  
```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```  
  
##  <a name="declare_view_status"></a>DECLARE_VIEW_STATUS  
 将此宏放在 ATL ActiveX 控件的控件类来指定**VIEWSTATUS**到容器的标志。  
  
```
DECLARE_VIEW_STATUS( statusFlags )
```  
  
### <a name="parameters"></a>参数  
 `statusFlags`  
 [in]**VIEWSTATUS**标志。 请参阅[VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201)的标志的列表。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Windowing #&126;](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)

