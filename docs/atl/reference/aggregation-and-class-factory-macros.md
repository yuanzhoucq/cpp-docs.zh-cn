---
title: 聚合和类工厂宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_AGGREGATABLE
- atlcom/ATL::DECLARE_CLASSFACTORY
- atlcom/ATL::DECLARE_CLASSFACTORY_EX
- atlcom/ATL::DECLARE_CLASSFACTORY_AUTO_THREAD
- atlcom/ATL::DECLARE_CLASSFACTORY_SINGLETON
- atlcom/ATL::DECLARE_GET_CONTROLLING_UNKNOWN
- atlcom/ATL::DECLARE_NOT_AGGREGATABLE
- atlcom/ATL::DECLARE_ONLY_AGGREGATABLE
- atlcom/ATL::DECLARE_POLY_AGGREGATABLE
- atlcom/ATL::DECLARE_PROTECT_FINAL_CONSTRUCT
- atlcom/ATL::DECLARE_VIEW_STATUS
helpviewer_keywords:
- class factories, ATL macros
- aggregation [C++], ATL macros
ms.assetid: d99d379a-0eec-481f-8daa-252dac18f163
ms.openlocfilehash: c0e3b6903e382ad56be9500792bec895a7641f00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497170"
---
# <a name="aggregation-and-class-factory-macros"></a>聚合和类工厂宏

这些宏提供控制聚合的并声明类工厂的方法。

|||
|-|-|
|[DECLARE_AGGREGATABLE](#declare_aggregatable)|声明您的对象可以是聚合 （默认值）。|
|[DECLARE_CLASSFACTORY](#declare_classfactory)|声明类工厂要[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，ATL 默认类工厂。|
|[DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)|声明类工厂对象是类工厂。|
|[DECLARE_CLASSFACTORY2](#declare_classfactory2)|声明[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)为类工厂。|
|[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)|声明[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)为类工厂。|
|[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)|声明[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)为类工厂。|
|[DECLARE_GET_CONTROLLING_UNKNOWN](#declare_get_controlling_unknown)|声明的虚拟`GetControllingUnknown`函数。|
|[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)|声明您的对象不能进行聚合。|
|[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)|声明必须聚合对象。|
|[DECLARE_POLY_AGGREGATABLE](#declare_poly_aggregatable)|检查外部未知的值，并可聚合或是不可聚合，根据需要声明您的对象。|
|[DECLARE_PROTECT_FINAL_CONSTRUCT](#declare_protect_final_construct)|内部对象的构造期间删除可防止外部对象。|
|[DECLARE_VIEW_STATUS](#declare_view_status)|指定对容器的 VIEWSTATUS 标志。|

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="declare_aggregatable"></a>  DECLARE_AGGREGATABLE

指定可聚合对象。

```
DECLARE_AGGREGATABLE( x )
```

### <a name="parameters"></a>参数

*x*<br/>
[in]可以定义为可聚合的类的名称。

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含此宏指定默认聚合模型。 若要重写此默认值，指定[DECLARE_NOT_AGGREGATABLE](#declare_not_aggregatable)或[DECLARE_ONLY_AGGREGATABLE](#declare_only_aggregatable)在类定义中的宏。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

##  <a name="declare_classfactory"></a>  DECLARE_CLASSFACTORY

声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)为类工厂。

```
DECLARE_CLASSFACTORY()
```

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)使用此宏来声明您的对象的默认类工厂。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#55](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_2.h)]

##  <a name="ccomclassfactory_class"></a>  CComClassFactory 类

此类实现[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)接口。

```
class CComClassFactory : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>备注

`CComClassFactory` 实现[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)接口，它包含用于创建特定的 CLSID 的对象，以及锁定的内存，这样更快地创建新对象中的类工厂方法。 `IClassFactory` 必须为每个类都可以注册在系统注册表中并向你分配 CLSID 实现。

ATL 对象通常通过继承获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)，其中声明`CComClassFactory`作为默认类工厂。 若要重写此默认值，指定一个 DECLARE_CLASSFACTORY*XXX*在类定义中的宏。 例如， [DECLARE_CLASSFACTORY_EX](#declare_classfactory_ex)宏类工厂使用指定的类：

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

上面的类定义指定`CMyClassFactory`将用作对象的默认类工厂。 `CMyClassFactory` 必须派生自`CComClassFactory`并重写`CreateInstance`。

ATL 提供了三个其他声明类工厂的宏：

- [DECLARE_CLASSFACTORY2](#declare_classfactory2)使用[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)，它可以控制创建通过许可证。

- [DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)使用[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)，用于在多个单元中创建对象。

- [DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)使用[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)，该构造一个[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)对象。

##  <a name="declare_classfactory_ex"></a>  DECLARE_CLASSFACTORY_EX

声明`cf`为类工厂。

```
DECLARE_CLASSFACTORY_EX( cf )
```

### <a name="parameters"></a>参数

*cf*<br/>
[in]实现您的类工厂对象的类的名称。

### <a name="remarks"></a>备注

*Cf*参数必须派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)并重写`CreateInstance`方法。

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏，它指定`CComClassFactory`作为默认类工厂。 但是，通过在对象的类定义中包括 DECLARE_CLASSFACTORY_EX 宏，你重写此默认值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_3.h)]

##  <a name="declare_classfactory2"></a>  DECLARE_CLASSFACTORY2

声明[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)为类工厂。

```
DECLARE_CLASSFACTORY2( lic )
```

### <a name="parameters"></a>参数

*许可证*<br/>
[in]实现的类`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏，它指定[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 但是，通过在对象的类定义中包括 DECLARE_CLASSFACTORY2 宏，你重写此默认值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

##  <a name="ccomclassfactory2_class"></a>  CComClassFactory2 类

此类实现[IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2)接口。

```
template <class license>
class  CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

### <a name="parameters"></a>参数

*许可证*<br/>
实现以下静态函数的类：

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

### <a name="remarks"></a>备注

`CComClassFactory2` 实现[IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2)接口，这是扩展的[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)。 `IClassFactory2` 控件通过许可证创建的对象。 已授权的计算机上类工厂执行可以提供运行时许可证密钥。 此许可证密钥允许应用程序的完整计算机许可证不存在时实例化对象。

ATL 对象通常通过继承获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)，其中声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 若要使用`CComClassFactory2`，指定[DECLARE_CLASSFACTORY2](#declare_classfactory2)对象的类定义中的宏。 例如：

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_4.h)]

`CMyLicense`模板参数`CComClassFactory2`，必须实现的静态函数`VerifyLicenseKey`， `GetLicenseKey`，和`IsLicenseValid`。 下面是简单的许可证类的一个示例：

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_5.h)]

`CComClassFactory2` 从这两个派生`CComClassFactory2Base`并*许可证*。 `CComClassFactory2Base`反过来，派生`IClassFactory2`并**CComObjectRootEx\< CComGlobalsThreadModel >**。

##  <a name="declare_classfactory_auto_thread"></a>  DECLARE_CLASSFACTORY_AUTO_THREAD

声明[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)为类工厂。

```
DECLARE_CLASSFACTORY_AUTO_THREAD()
```

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏，它指定[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 但是，通过在对象的类定义中包括 DECLARE_CLASSFACTORY_AUTO_THREAD 宏，你重写此默认值。

创建对象时在多个单元 （在的进程服务器） 中将 DECLARE_CLASSFACTORY_AUTO_THREAD 添加到您的类。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

##  <a name="ccomclassfactoryautothread_class"></a>  CComClassFactoryAutoThread 类

此类实现[IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory)接口，并允许在多个单元中创建的对象。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

```
class CComClassFactoryAutoThread : public IClassFactory,
public CComObjectRootEx<CComGlobalsThreadModel>
```

### <a name="remarks"></a>备注

`CComClassFactoryAutoThread` 类似于[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，但允许在多个单元中创建的对象。 若要充分利用此支持，派生从 EXE 模块[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)。

ATL 对象通常通过继承获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)，其中声明[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 若要使用`CComClassFactoryAutoThread`，指定[DECLARE_CLASSFACTORY_AUTO_THREAD](#declare_classfactory_auto_thread)对象的类定义中的宏。 例如：

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_6.h)]

##  <a name="declare_classfactory_singleton"></a>  DECLARE_CLASSFACTORY_SINGLETON

声明[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)为类工厂。

```
DECLARE_CLASSFACTORY_SINGLETON( obj )
```

### <a name="parameters"></a>参数

*obj*<br/>
[in]类对象的名称。

### <a name="remarks"></a>备注

[CComCoClass](../../atl/reference/ccomcoclass-class.md)包括[DECLARE_CLASSFACTORY](#declare_classfactory)宏，它指定[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)作为默认类工厂。 但是，通过在对象的类定义中包括 DECLARE_CLASSFACTORY_SINGLETON 宏，你重写此默认值。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

##  <a name="ccomclassfactorysingleton_class"></a>  CComClassFactorySingleton 类

此类派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)构造一个单一对象。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

### <a name="parameters"></a>参数

*T*<br/>
您的类。

`CComClassFactorySingleton` 派生自[CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ，并使用[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)构造一个单一对象。 每次调用`CreateInstance`方法只需将查询此对象的接口指针。

### <a name="remarks"></a>备注

ATL 对象通常通过继承获取类工厂[CComCoClass](../../atl/reference/ccomcoclass-class.md)。 此类包括宏[DECLARE_CLASSFACTORY](#declare_classfactory)，其中声明`CComClassFactory`作为默认类工厂。 若要使用`CComClassFactorySingleton`，指定[DECLARE_CLASSFACTORY_SINGLETON](#declare_classfactory_singleton)对象的类定义中的宏。 例如：

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_7.h)]

##  <a name="declare_get_controlling_unknown"></a>  DECLARE_GET_CONTROLLING_UNKNOWN

将虚拟函数声明`GetControllingUnknown`。

```
DECLARE_GET_CONTROLLING_UNKNOWN()
```

### <a name="remarks"></a>备注

将此宏添加到您的对象，如果收到编译器错误消息`GetControllingUnknown`是不确定的 (例如，在`CComAggregateCreator`)。

##  <a name="declare_not_aggregatable"></a>  DECLARE_NOT_AGGREGATABLE

指定您的对象不能进行聚合。

```
DECLARE_NOT_AGGREGATABLE( x )
```

### <a name="parameters"></a>参数

*x*<br/>
[in]可以定义为不可聚合的类对象的名称。

### <a name="remarks"></a>备注

DECLARE_NOT_AGGREGATABLE 导致`CreateInstance`如果尝试返回错误 (CLASS_E_NOAGGREGATION) 到您的对象上的聚合。

默认情况下[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)宏，指定可聚合对象。 若要重写此默认行为，请在类定义中包含 DECLARE_NOT_AGGREGATABLE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#121](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_1.h)]

##  <a name="declare_only_aggregatable"></a>  DECLARE_ONLY_AGGREGATABLE

指定必须聚合对象。

```
DECLARE_ONLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>参数

*x*<br/>
[in]可以定义为仅可聚合的类对象的名称。

### <a name="remarks"></a>备注

DECLARE_ONLY_AGGREGATABLE 会导致错误 (E_FAIL)，如果尝试为`CoCreate`您作为非聚合对象的对象。

默认情况下[CComCoClass](../../atl/reference/ccomcoclass-class.md)包含[DECLARE_AGGREGATABLE](#declare_aggregatable)宏，指定可聚合对象。 若要重写此默认行为，请在类定义中包含 DECLARE_ONLY_AGGREGATABLE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#125](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_8.h)]

##  <a name="declare_poly_aggregatable"></a>  DECLARE_POLY_AGGREGATABLE

指定的实例**CComPolyObject \<**  *x* **>** 创建您的对象时创建。

```
DECLARE_POLY_AGGREGATABLE( x )
```

### <a name="parameters"></a>参数

*x*<br/>
[in]可以定义为可聚合或是不可聚合的类对象的名称。

### <a name="remarks"></a>备注

在创建期间，检查外部未知的值。 如果值为 NULL，`IUnknown`为非聚合对象实现。 如果未知的外部不为 NULL，`IUnknown`为聚合对象实现。

使用 DECLARE_POLY_AGGREGATABLE 的优点是，你就可以避免这两`CComAggObject`和`CComObject`处理聚合和非聚合的情况下在模块中。 单个`CComPolyObject`对象将处理这两种情况。 这意味着你的模块中存在的 vtable 只有一个副本和函数的一个副本。 如果你 vtable 很大，这可以显著减少模块大小。 但是，如果你 vtable 很小，则使用`CComPolyObject`可能导致稍大模块大小，因为它不优化聚合或非聚合对象，因为`CComAggObject`和`CComObject`。

如果使用 ATL 控件向导来创建完全控制，DECLARE_POLY_AGGREGATABLE 宏自动声明在对象中。

##  <a name="declare_protect_final_construct"></a>  DECLARE_PROTECT_FINAL_CONSTRUCT

如果删除保护您的对象 (期间[FinalConstruct](ccomobjectrootex-class.md#finalconstruct)) 内部聚合的对象递增引用计数则递减为 0 的计数。

```
DECLARE_PROTECT_FINAL_CONSTRUCT()
```

##  <a name="declare_view_status"></a>  DECLARE_VIEW_STATUS

将此宏放置在 ATL ActiveX 控件的控件类，以指定对容器的 VIEWSTATUS 标志。

```
DECLARE_VIEW_STATUS( statusFlags )
```

### <a name="parameters"></a>参数

*statusFlags*<br/>
[in]VIEWSTATUS 标志中。 请参阅[VIEWSTATUS](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus)标志的列表。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#126](../../atl/codesnippet/cpp/aggregation-and-class-factory-macros_9.h)]

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
