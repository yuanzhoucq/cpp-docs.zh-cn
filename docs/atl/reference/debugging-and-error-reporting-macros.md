---
title: 调试和错误报告宏
ms.date: 05/06/2019
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
ms.openlocfilehash: 69ab6e17bfb1ec85ddb5b8c19c18010a9b4f3df6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330189"
---
# <a name="debugging-and-error-reporting-macros"></a>调试和错误报告宏

这些宏提供有用的调试和跟踪工具。

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|写入输出窗口时检测到`_Module.Term`的任何接口泄漏。|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|将所有调用写入`QueryInterface`输出窗口。|
|[ATLASSERT](#atlassert)|执行与 C 运行时[库中_ASSERTE宏](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)相同的功能。|
|[ATLENSURE](#atlensure)|执行参数验证。 如果需要`AtlThrow`，请致电|
|[ATLTRACENOTIMPL](#atltracenotimpl)|向转储设备发送消息，指出未实现指定的功能。|
|[ATLTRACE](#atltrace)|根据指示的标志和级别向输出设备（如调试器窗口）报告警告。 包括用于向后兼容性。|
|[ATLTRACE2](#atltrace2)|根据指示的标志和级别向输出设备（如调试器窗口）报告警告。|

## <a name="_atl_debug_interfaces"></a><a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES

在包含任何 ATL 标头文件以跟踪组件接口`AddRef`上`Release`的所有和调用到输出窗口之前，请定义此宏。

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>备注

跟踪输出将显示如下：

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

每个跟踪的第一部分将始终为`ATL: QIThunk`。 接下来是标识正在使用的特定*接口 thunk*的值。 接口 thunk 是用于维护引用计数并提供此处使用的跟踪功能的对象。 `QueryInterface`除了`IUnknown`对接口的请求（在这种情况下，每次返回相同的 thunk 以遵守 COM 的标识规则），每次调用 时都会创建一个新的接口 thunk。

接下来，您将看到`AddRef`或`Release`指示调用了哪种方法。 之后，您将看到一个值，用于标识其接口引用计数已更改的对象。 跟踪的值是对象的**此**指针。

跟踪的引用计数是调用或`AddRef``Release`调用后该 thunk 上的引用计数。 请注意，此引用计数可能与对象的引用计数不匹配。 每个 thunk 都维护自己的引用计数，以帮助您完全遵守 COM 的引用计数规则。

跟踪的最后一条信息是对象的名称和受`AddRef`或`Release`调用影响的接口。

服务器关闭并`_Module.Term`调用时检测到的任何接口泄漏都将记录如下：

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

此处提供的信息直接映射到前面的跟踪语句中提供的信息，因此您可以检查接口 thunk 的整个生存期内的引用计数。 此外，您还可以显示该接口 thunk 上的最大引用计数。

> [!NOTE]
> _ATL_DEBUG_INTERFACES可用于零售版本。

## <a name="_atl_debug_qi"></a><a name="_atl_debug_qi"></a>_ATL_DEBUG_QI

将所有调用写入`QueryInterface`输出窗口。

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>备注

如果对`QueryInterface`呼叫失败，输出窗口将显示：

*接口名称* - `failed`

## <a name="atlassert"></a><a name="atlassert"></a>ATLASSERT

ATLASSERT 宏执行的功能与 C 运行时库中的[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)宏相同。

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>参数

*布尔表达式*<br/>
计算结果为零或不为零的表达式（包括指针）。

### <a name="remarks"></a>备注

在调试生成中，ATLASSERT 会评估*布尔表达式*，并在结果为 false 时生成调试报告。

## <a name="requirements"></a>要求

**标题：** atldef.h

## <a name="atlensure"></a><a name="atlensure"></a>ATLENSURE

此宏用于验证传递给函数的参数。

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>参数

*布尔表达式*<br/>
指定要测试的布尔表达式。

*人力资源*<br/>
指定要返回的错误代码。

### <a name="remarks"></a>备注

这些宏提供了一种机制来检测和通知用户不正确的参数使用。

宏调用 ATLASSERT，如果条件失败调用`AtlThrow`。

在 ATLENSURE 的情况下`AtlThrow`，用E_FAIL调用。

在ATLENSURE_THROW情况下，`AtlThrow`使用指定的 HRESULT 调用。

ATLENSURE 和 ATLASSERT 之间的区别在于 ATLENSURE 在发布版本和调试版本中引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="atltracenotimpl"></a><a name="atltracenotimpl"></a>ATLTRACENOTIMPL

在 ATL 的调试版本中，将字符串"未实现*funcname"* 发送到转储设备并返回E_NOTIMPL。

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>参数

*乐趣名称*<br/>
[在]包含未实现的函数的名称的字符串。

### <a name="remarks"></a>备注

在版本生成中，只需返回E_NOTIMPL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>要求

**标题：** atltrace.h

## <a name="atltrace"></a><a name="atltrace"></a>ATLTRACE

根据指示的标志和级别向输出设备（如调试器窗口）报告警告。 包括用于向后兼容性。

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>参数

*exp*<br/>
[在]要发送到输出窗口或任何陷印这些消息的应用程序的字符串和变量。

*类别*<br/>
[在]要报告的事件或方法的类型。 有关类别列表，请参阅备注。

*水平*<br/>
[在]要报告的跟踪级别。 有关详细信息，请参阅备注。

*lpsz格式*<br/>
[在]要发送到转储设备的格式化字符串。

### <a name="remarks"></a>备注

有关 ATLTRACE 的说明，请参阅[ATLTRACE2。](#atltrace2) ATLTRACE 和 ATLTRACE2 具有相同的行为，ATLTRACE 包含在向后兼容性中。

## <a name="atltrace2"></a><a name="atltrace2"></a>ATLTRACE2

根据指示的标志和级别向输出设备（如调试器窗口）报告警告。

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTR lpszFormat,  ...);
```

### <a name="parameters"></a>参数

*exp*<br/>
[在]要发送到输出窗口或任何陷印这些消息的应用程序的字符串。

*类别*<br/>
[在]要报告的事件或方法的类型。 有关类别列表，请参阅备注。

*水平*<br/>
[在]要报告的跟踪级别。 有关详细信息，请参阅备注。

*lpsz格式*<br/>
[在]用于`printf`创建要发送到转储设备的字符串的 -style 格式字符串。

### <a name="remarks"></a>备注

ATLTRACE2 的短形式将字符串写入调试器的输出窗口。 ATLTRACE2 的第二种形式还会将输出写入调试器的输出窗口，但受 ATL/MFC 跟踪工具的设置的约束（请参阅[ATLTraceTool 示例](../../overview/visual-cpp-samples.md)）。 例如，如果将*级别*设置为 4，将 ATL/MFC 跟踪工具设置为级别 0，则看不到消息。 *级别*可以是 0、1、2、3 或 4。 默认值 0 仅报告最严重的问题。

*类别*参数列出要设置的跟踪标志。 这些标志对应于要为其报告的方法类型。 下表列出了可用于*类别*参数的有效跟踪标志。

### <a name="atl-trace-flags"></a>ATL 跟踪标志

|ATL 类别|说明|
|------------------|-----------------|
|`atlTraceGeneral`|所有 ATL 应用程序的报告。 默认值。|
|`atlTraceCOM`|有关 COM 方法的报告。|
|`atlTraceQI`|有关查询接口调用的报告。|
|`atlTraceRegistrar`|关于对象注册的报告。|
|`atlTraceRefcount`|关于更改引用计数的报告。|
|`atlTraceWindowing`|关于窗口方法的报告;例如，报告无效的消息映射 ID。|
|`atlTraceControls`|关于控制的报告;例如，当控件或其窗口被销毁时，报告。|
|`atlTraceHosting`|报告托管消息;例如，当容器中的客户端被激活时，将报告。|
|`atlTraceDBClient`|有关 OLE DB 使用者模板的报告;例如，当对 GetData 的调用失败时，输出可以包含 HRESULT。|
|`atlTraceDBProvider`|有关 OLE DB 提供程序模板的报告;例如，如果创建列失败，则报告。|
|`atlTraceSnapin`|MMC SnapIn 应用程序的报告。|
|`atlTraceNotImpl`|报告未实现指示的功能。|
|`atlTraceAllocation`|报告由 atldbgmem.h 中的内存调试工具打印的消息。|

### <a name="mfc-trace-flags"></a>MFC 跟踪标志

|MFC 类别|说明|
|------------------|-----------------|
|`traceAppMsg`|一般用途，MFC 消息。 始终推荐。|
|`traceDumpContext`|来自[CDumpContext 的消息](../../mfc/reference/cdumpcontext-class.md)。|
|`traceWinMsg`|来自 MFC 消息处理代码的消息。|
|`traceMemory`|来自 MFC 内存管理代码的消息。|
|`traceCmdRouting`|来自 MFC 的 Windows 命令路由代码的消息。|
|`traceHtml`|来自 MFC 的 DHTML 对话框支持的消息。|
|`traceSocket`|来自 MFC 的套接字支持的消息。|
|`traceOle`|来自 MFC OLE 支持的消息。|
|`traceDatabase`|来自 MFC 数据库支持的消息。|
|`traceInternet`|来自 MFC 互联网支持的消息。|

要声明自定义跟踪类别，可以声明类的全局实例，`CTraceCategory`如下所示：

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

在本示例中MY_CATEGORY类别名称是您为*类别*参数指定的名称。 第一个参数是将出现在 ATL/MFC 跟踪工具中的类别名称。 第二个参数是默认跟踪级别。 此参数是可选的，默认跟踪级别为 0。

要使用用户定义的类别：

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

若要指定要筛选跟踪消息，请在语句之前将这些宏的定义插入到 Stdafx.h 中`#include <atlbase.h>`。

或者，您可以在 **"属性页**"对话框中的预处理器指令中设置筛选器。 单击 **"预处理器**"选项卡，然后将全局插入到 **"预处理器定义**"编辑框中。

Atlbase.h 包含 ATLTRACE2 宏的默认定义，如果您在处理 atlbase.h 之前未定义这些符号，将使用这些定义。

在版本版本中，ATLTRACE2 编译到`(void) 0`。

ATLTRACE2 将要发送到转储设备的字符串的内容限制在格式化后不超过 1023 个字符。

ATLTRACE 和 ATLTRACE2 具有相同的行为，ATLTRACE 包含在向后兼容性中。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)<br/>
[调试和错误报告全局函数](../../atl/reference/debugging-and-error-reporting-global-functions.md)
