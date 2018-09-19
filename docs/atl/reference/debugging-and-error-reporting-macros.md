---
title: 调试和错误报告宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
dev_langs:
- C++
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fc187cea874d16522955dcd46c2ceac34d29098
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136150"
---
# <a name="debugging-and-error-reporting-macros"></a>调试和错误报告宏

这些宏提供有用的调试和跟踪工具。

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|写入到输出窗口中，任何界面泄漏时检测到`_Module.Term`调用。|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|将写入到的所有调用`QueryInterface`到输出窗口。|
|[ATLASSERT](#atlassert)|执行相同的功能[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)宏 C 运行时库中找到。|
|[ATLENSURE](#atlensure)|执行参数验证。 调用`AtlThrow`必要|
|[ATLTRACENOTIMPL](#atltracenotimpl)|将消息发送到转储设备未实现指定的函数。|
|[ATLTRACE](#alttrace)|报告到输出设备，如调试器窗口中，根据所指示的标志和级别的警告。 包含用于向后兼容。|
|[ATLTRACE2](#atltrace2)|报告到输出设备，如调试器窗口中，根据所指示的标志和级别的警告。|

##  <a name="_atl_debug_interfaces"></a>  _ATL_DEBUG_INTERFACES

包含任何要跟踪所有的 ATL 标头文件之前先定义此宏`AddRef`和`Release`调用组件的接口连接到输出窗口上。

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>备注

跟踪输出将显示如下所示：

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

每个跟踪的第一个部分始终为`ATL: QIThunk`。 接下来是一个标识特定的值*接口转换 （thunk）* 正在使用。 接口转换 （thunk） 是用来维护引用计数并提供此处使用的跟踪功能的对象。 在每次调用创建一个新接口 thunk`QueryInterface`除外的请求`IUnknown`接口 （在这种情况下，相同的转换 （thunk） 返回每次都要遵循的 COM 的标识规则）。

接下来你将看到`AddRef`或`Release`，该值指示调用的方法。 接下来，你将看到一个标识其接口引用计数已更改的对象的值。 跟踪的值是**这**对象的指针。

是否在跟踪的引用计数是后该转换 （thunk） 的引用计数`AddRef`或`Release`调用。 请注意，此引用计数可能不匹配的对象的引用计数。 每个转换 （thunk） 维护其自身的引用计数，以帮助您完全符合 COM 的引用计数规则。

跟踪的信息的最后一个部分是对象和受影响的接口的名称`AddRef`或`Release`调用。

当服务器关闭时检测到的泄漏的任何接口和`_Module.Term`调用后将会记录如下：

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

直接映射到以前的跟踪语句中提供的信息此处提供的信息，以便你可以检查的引用计数整个接口转换 （thunk） 的整个生存期。 此外，该接口转换 （thunk） 上获得最大引用计数的指示。

> [!NOTE]
> 在零售版本中，可以使用 _ATL_DEBUG_INTERFACES。

##  <a name="_atl_debug_qi"></a>  _ATL_DEBUG_QI

将写入到的所有调用`QueryInterface`到输出窗口。

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>备注

如果调用`QueryInterface`失败，将显示输出窗口：

*接口名称* - `failed`

##  <a name="atlassert"></a>  ATLASSERT

ATLASSERT 宏执行相同的功能[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)宏 C 运行时库中找到。

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>参数

*布尔表达式*<br/>
计算结果为零或不为零的表达式（包括指针）。

### <a name="remarks"></a>备注

在调试版本中，计算 ATLASSERT*布尔表达式*并在结果为 false 时生成调试报告。  

## <a name="requirements"></a>要求

**标头：** atldef.h

##  <a name="atlensure"></a>  ATLENSURE

此宏用于验证传递给函数的参数。

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>参数

*布尔表达式*<br/>
指定要测试的布尔表达式。

*hr*<br/>
指定要返回的错误代码。

### <a name="remarks"></a>备注

这些宏提供一种机制来检测并通知用户的不正确的参数的用法。

宏将调用 ATLASSERT 和如果条件失败时调用`AtlThrow`。

在 ATLENSURE 情况下，`AtlThrow`称为 E_FAIL。

在 ATLENSURE_THROW 情况下，`AtlThrow`调用使用指定的 HRESULT。

ATLENSURE 和 ATLASSERT 之间的区别是 ATLENSURE 发布版本以及调试版本中引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]  

## <a name="requirements"></a>要求

**标头：** afx.h  

##  <a name="atltracenotimpl"></a>  ATLTRACENOTIMPL

在 ATL 的调试版本中，将字符串" *funcname*未实现"转储设备和返回 E_NOTIMPL。

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>参数

*函数名*<br/>
[in]包含未实现的函数名称的字符串。

### <a name="remarks"></a>备注

在发布版本中，只需返回 E_NOTIMPL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>要求

**标头：** atltrace.h 

##  <a name="atltrace"></a>  ATLTRACE

报告到输出设备，如调试器窗口中，根据所指示的标志和级别的警告。 包含用于向后兼容。

```
ATLTRACE(exp);

ATLTRACE(  
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>参数

*exp*<br/>
[in]字符串和要发送到 Visual c + + 输出窗口或捕获这些消息的任何应用程序的变量。

*category*<br/>
[in]事件或在其上报告的方法的类型。 请参阅备注类别的列表。

*级别*<br/>
[in]对报表的跟踪级别。 请参阅备注以了解详情。

*lpszFormat*<br/>
[in]要将发送到转储设备的格式化的字符串。

### <a name="remarks"></a>备注

请参阅[ATLTRACE2](#atltrace2) ATLTRACE 的说明。 ATLTRACE 和 ATLTRACE2 具有相同的行为，ATLTRACE 是为了向后兼容。

##  <a name="atltrace2"></a>  ATLTRACE2

报告到输出设备，如调试器窗口中，根据所指示的标志和级别的警告。

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```

### <a name="parameters"></a>参数

*exp*<br/>
[in]要将发送到 Visual c + + 输出窗口或捕获这些消息的任何应用程序的字符串。

*category*<br/>
[in]事件或在其上报告的方法的类型。 请参阅备注类别的列表。

*级别*<br/>
[in]对报表的跟踪级别。 请参阅备注以了解详情。

*lpszFormat*<br/>
[in]`printf`-设置要用于创建要发送到转储设备的字符串的格式字符串的样式。

### <a name="remarks"></a>备注

ATLTRACE2 的缩写形式将字符串写入调试器的输出窗口。 ATLTRACE2 第二种形式还将输出写入到调试器的输出窗口中，但可能会发生的 ATL/MFC 跟踪工具的设置 (请参阅[ATLTraceTool 示例](../../visual-cpp-samples.md))。 例如，如果您设置*级别*到 4 和 ATL/MFC 跟踪工具到级别 0 中，不会看到消息。 *级别*可以是 0、 1、 2、 3 或 4。 默认情况下，0，报告最严重的问题。

*类别*参数列出了要设置的跟踪标志。 这些标志对应于为其您要报告的方法的类型。 以下各表列出可用于有效的跟踪标志*类别*参数。

### <a name="atl-trace-flags"></a>ATL 跟踪标志

|ATL 类别|描述|
|------------------|-----------------|
|`atlTraceGeneral`|所有 ATL 应用程序的报表。 默认值。|
|`atlTraceCOM`|COM 方法的报表。|
|`atlTraceQI`|QueryInterface 调用的报表。|
|`atlTraceRegistrar`|此注册对象的报表。|
|`atlTraceRefcount`|更改引用计数的报表。|
|`atlTraceWindowing`|报表上 windows 方法;例如，报告无效的消息映射 id。|
|`atlTraceControls`|控件; 上的报表例如，报告时销毁控件或它的窗口。|
|`atlTraceHosting`|报表承载消息;例如，报告激活容器中的客户端时。|
|`atlTraceDBClient`|OLE DB 使用者模板; 上的报表例如，在调用 GetData 失败，输出可以包含 HRESULT。|
|`atlTraceDBProvider`|OLE DB 提供程序模板; 上的报表例如，报告的列的创建失败，如果。|
|`atlTraceSnapin`|MMC 管理单元应用程序的报表。|
|`atlTraceNotImpl`|报告未实现所指示的函数。|
|`atlTraceAllocation`|报表打印 atldbgmem.h 中的调试工具的内存的消息。|

### <a name="mfc-trace-flags"></a>MFC 跟踪标志

|MFC 类别|描述|
|------------------|-----------------|
|`traceAppMsg`|常规用途，MFC 消息。 始终建议。|
|`traceDumpContext`|从消息[CDumpContext](../../mfc/reference/cdumpcontext-class.md)。|
|`traceWinMsg`|MFC 的消息处理代码中的消息。|
|`traceMemory`|MFC 的内存管理代码中的消息。|
|`traceCmdRouting`|从 MFC 的 Windows 消息的命令路由的代码。|
|`traceHtml`|MFC 的 DHTML 对话框支持中的消息。|
|`traceSocket`|MFC 的套接字支持中的消息。|
|`traceOle`|从 MFC 的 OLE 支持的消息。|
|`traceDatabase`|从 MFC 数据库支持的消息。|
|`traceInternet`|从 MFC 的 Internet 支持的消息。|

若要声明自定义跟踪类别，声明的全局实例`CTraceCategory`类，如下所示：

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

类别名称，在此示例中，MY_CATEGORY 是到指定的名称*类别*参数。 第一个参数是会在 ATL/MFC 跟踪工具中显示的类别名称。 第二个参数是默认跟踪级别。 此参数是可选的并且默认跟踪级别为 0。

若要使用用户定义的类别：

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

若要指定你想要筛选跟踪消息，将这些宏的定义 Stdafx.h 之前插入`#include <atlbase.h>`语句。

或者，可以设置筛选器中的预处理器指令中**属性页**对话框。 单击**预处理器**选项卡，然后插入到全局**预处理器定义**编辑框。

Atlbase.h 包含 ATLTRACE2 宏的默认定义，如果未定义这些符号 atlbase.h 处理之前，将使用这些定义。

在发布版本中将编译为的 ATLTRACE2 `(void) 0`。

ATLTRACE2 限制要发送到转储设备，不能超过 1023年个字符，来设置格式后的字符串的内容。

ATLTRACE 和 ATLTRACE2 具有相同的行为，ATLTRACE 是为了向后兼容。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)<br/>
[调试和错误报告全局函数](../../atl/reference/debugging-and-error-reporting-global-functions.md)
