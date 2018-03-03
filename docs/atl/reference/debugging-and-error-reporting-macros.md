---
title: "调试和错误报告的宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9098b944f70ab4e4448fe40aa2347b0128e6e1a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-error-reporting-macros"></a>调试和错误报告的宏
这些宏提供有用的调试和跟踪功能。  
  
|||  
|-|-|  
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|将任何接口泄漏，写入输出窗口中，当检测到`_Module.Term`调用。|  
|[_ATL_DEBUG_QI](#_atl_debug_qi)|写入到的所有调用`QueryInterface`到输出窗口。|  
|[ATLASSERT](#atlassert)|执行与相同的功能[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)宏 C 运行时库中找到。|  
|[ATLENSURE](#atlensure)|执行参数验证。 调用`AtlThrow`必要|  
|[ATLTRACENOTIMPL](#atltracenotimpl)|将消息发送到转储设备未实现指定的函数。|  
|[ATLTRACE](#alttrace)|将报告警告输出设备，如调试器窗口中，根据指定的标志和级别。 包括的向后兼容性。|  
|[ATLTRACE2](#atltrace2)|将报告警告输出设备，如调试器窗口中，根据指定的标志和级别。|  
  
##  <a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES  
 包括任何要跟踪所有的 ATL 标头文件之前，定义此宏`AddRef`和**版本**在你的组件的接口连接到输出窗口上调用。  
  
```
#define _ATL_DEBUG_INTERFACES
```  
  
### <a name="remarks"></a>备注  
 跟踪输出将显示如下所示：  
  
 `ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`  
  
 每个跟踪的第一部分始终会`ATL: QIThunk`。 接下来是一个值，标识特定*接口转换 （thunk）*正在使用。 接口转换 （thunk） 是用于维护引用计数，并提供此处使用的跟踪功能的对象。 在每次调用创建一个新的接口 thunk`QueryInterface`除外请求**IUnknown**接口 （在这种情况下，相同的转换 （thunk） 返回每次以符合 COM 的标识规则）。  
  
 接下来你将看到`AddRef`或**版本**，该值指示调用哪个方法。 接下来，你将看到一个标识已更改其接口引用计数的对象的值。 跟踪的值是**这**的对象的指针。  
  
 为跟踪的引用计数是后该转换 （thunk） 上的引用计数`AddRef`或**版本**调用。 请注意此引用计数可能不匹配的对象的引用计数。 每个转换 （thunk） 将保持其自身的引用计数，来帮助你完全符合 COM 的引用计数规则。  
  
 跟踪的信息的最后一个部分是对象以及所影响的接口名称`AddRef`或**版本**调用。  
  
 当服务器关闭时检测到泄漏的任何接口和`_Module.Term`调用将会记录如下：  
  
 `ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`  
  
 映射到前面的跟踪语句中提供的信息直接此处提供的信息，以便你可以检查的引用计数整个接口转换 （thunk） 的整个生命周期。 此外，该接口转换 （thunk） 上获取最大引用计数的指示。  
  
> [!NOTE]
> `_ATL_DEBUG_INTERFACES`可在零售版本。  
  
##  <a name="_atl_debug_qi"></a>_ATL_DEBUG_QI  
 写入到的所有调用`QueryInterface`到输出窗口。  
  
```
#define _ATL_DEBUG_QI
```  
  
### <a name="remarks"></a>备注  
 如果调用`QueryInterface`失败，将显示输出窗口：  
  
 *接口名称* - `failed`  
  
##  <a name="atlassert"></a>ATLASSERT  
 `ATLASSERT`宏执行与相同的功能[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)宏 C 运行时库中找到。  
  
```
ATLASSERT(booleanExpression);
```  
  
### <a name="parameters"></a>参数  
 `booleanExpression`  
 计算结果为零或不为零的表达式（包括指针）。  
  
### <a name="remarks"></a>备注  
 在调试版本中，`ATLASSERT`计算结果`booleanExpression`和结果为 false 时，将生成调试报告。  

## <a name="requirements"></a>惠?  
 **标头：** atldef.h  
    
##  <a name="atlensure"></a>ATLENSURE  
 此宏用于验证传递给函数的参数。  
  
```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```  
  
### <a name="parameters"></a>参数  
 `booleanExpression`  
 指定要测试的布尔表达式。  
  
 `hr`  
 指定要返回错误代码。  
  
### <a name="remarks"></a>备注  
 这些宏提供一种机制来检测和通知不正确的参数用法的用户。  
  
 宏调用`ATLASSERT`和如果该条件未调用`AtlThrow`。  
  
 在**ATLENSURE**情况下， `AtlThrow` E_FAIL 已调用。  
  
 在**ATLENSURE_THROW**情况下，`AtlThrow`已调用指定的 HRESULT。  
  
 之间的差异**ATLENSURE**和`ATLASSERT`在于**ATLENSURE**引发版本中的异常以及生成如下所示的调试版本。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]  

## <a name="requirements"></a>惠?  
 **标头：** afx.h  

##  <a name="atltracenotimpl"></a>ATLTRACENOTIMPL  
 ATL 的调试版本中发送字符串"`funcname`未实现"转储设备并返回到**E_NOTIMPL**。  
  
```
ATLTRACENOTIMPL(funcname);
```  
  
### <a name="parameters"></a>参数  
 `funcname`  
 [in]包含未实现的函数名称的字符串。  
  
### <a name="remarks"></a>备注  
 在发布版本，只需返回**E_NOTIMPL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]  
  
## <a name="requirements"></a>惠?  
 **标头：** atltrace.h 

##  <a name="atltrace"></a>ATLTRACE
 将报告警告输出设备，如调试器窗口中，根据指定的标志和级别。 包括的向后兼容性。  
  
```
ATLTRACE(exp);

ATLTRACE(  
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```  
  
### <a name="parameters"></a>参数  
 `exp`  
 [in]字符串和要发送到 Visual c + + 输出窗口或任何应用程序捕获这些消息的变量。  
  
 `category`  
 [in]事件或在其上的方法来报告的类型。 请参阅有关类别的列表的备注部分。  
  
 `level`  
 [in]对报表的跟踪级别。 请参阅备注以了解详情。  
  
 `lpszFormat`  
 [in]要将发送到转储设备的格式化的字符串。  
  
### <a name="remarks"></a>备注  
 请参阅[ATLTRACE2](#atltrace2)有关的说明**ATLTRACE**。 **ATLTRACE**和`ATLTRACE2`具有相同的行为， **ATLTRACE**包含是为了向后兼容。  
  
##  <a name="atltrace2"></a>ATLTRACE2  
 将报告警告输出设备，如调试器窗口中，根据指定的标志和级别。  
  
```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```  
  
### <a name="parameters"></a>参数  
 `exp`  
 [in]要将发送到 Visual c + + 输出窗口或任何应用程序捕获这些消息的字符串。  
  
 `category`  
 [in]事件或在其上的方法来报告的类型。 请参阅有关类别的列表的备注部分。  
  
 `level`  
 [in]对报表的跟踪级别。 请参阅备注以了解详情。  
  
 `lpszFormat`  
 [in]`printf`-设置要用于创建要发送到转储设备字符串的格式字符串的样式。  
  
### <a name="remarks"></a>备注  
 缩写形式`ATLTRACE2`写入到调试器的字符串的输出窗口。 第二种形式的`ATLTRACE2`还将输出写入到调试器的输出窗口，但可能会发生的 ATL/MFC 跟踪工具的设置 (请参阅[ATLTraceTool 示例](../../visual-cpp-samples.md))。 例如，如果你设置`level`4 和 ATL/MFC 跟踪工具到级别 0，不将看到消息。 *级别*可以是 0、 1、 2、 3 或 4。 默认情况下，0，报告最严重的问题。  
  
 `category`参数列出要设置的跟踪标志。 这些标志对应于为其要报告的方法的类型。 下表列出可用于的有效的跟踪标志`category`参数。  
  
### <a name="atl-trace-flags"></a>ATL 跟踪标志  
  
|ATL 类别|描述|  
|------------------|-----------------|  
|`atlTraceGeneral`|所有 ATL 应用程序的报表。 默认值。|  
|`atlTraceCOM`|在 COM 方法上的报表。|  
|`atlTraceQI`|QueryInterface 调用的报表。|  
|`atlTraceRegistrar`|对象注册的报表。|  
|`atlTraceRefcount`|更改引用计数的报表。|  
|`atlTraceWindowing`|有关 windows 方法; 这些方法的报告例如，报告一个无效的消息映射 id。|  
|`atlTraceControls`|控件; 上的报表例如，报告的控件或其窗口时销毁。|  
|`atlTraceHosting`|承载消息; 的报表例如，报告激活容器中的客户端时。|  
|`atlTraceDBClient`|在 OLE DB 使用者模板; 上的报表例如，当 GetData 失败的调用中，输出可以包含 HRESULT。|  
|`atlTraceDBProvider`|在 OLE DB 提供程序模板; 上的报表例如，报告如果列的创建失败。|  
|`atlTraceSnapin`|MMC 管理单元应用程序的报表。|  
|`atlTraceNotImpl`|报告指示的函数未实现。|  
|**atlTraceAllocation**|报表打印 atldbgmem.h 中的调试工具的内存的消息。|  
  
### <a name="mfc-trace-flags"></a>MFC 跟踪标志  
  
|MFC 类别|描述|  
|------------------|-----------------|  
|**traceAppMsg**|一般用途，MFC 消息。 始终建议。|  
|**traceDumpContext**|从消息[CDumpContext](../../mfc/reference/cdumpcontext-class.md)。|  
|**traceWinMsg**|从 MFC 的消息处理代码的消息。|  
|**traceMemory**|从 MFC 的内存管理代码的消息。|  
|**traceCmdRouting**|从 MFC 的 Windows 消息命令路由的代码。|  
|**traceHtml**|MFC 的 DHTML 对话框支持发送的消息。|  
|**traceSocket**|从 MFC 的套接字支持的消息。|  
|**traceOle**|从 MFC 的 OLE 支持的消息。|  
|**traceDatabase**|从 MFC 的数据库支持的消息。|  
|**traceInternet**|从 MFC 的 Internet 支持的消息。|  
  
 若要声明自定义跟踪类别，声明的全局实例`CTraceCategory`类，如下所示：  
  
 [!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]  
  
 类别名称，`MY_CATEGORY`在此示例中，是你可以指定的名称`category`参数。 第一个参数是会在 ATL/MFC 跟踪工具中显示的类别名称。 第二个参数是默认跟踪级别。 此参数是可选的并且默认跟踪级别为 0。  
  
 若要使用用户定义的类别：  
  
 [!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]  
  
 若要指定你想要筛选跟踪消息，将这些宏的定义 Stdafx.h 之前插入`#include <atlbase.h>`语句。  
  
 或者，可以设置筛选器中的预处理器指令中**属性页**对话框。 单击**预处理器**选项卡上，然后插入到全局**预处理器定义**编辑框。  
  
 Atlbase.h 包含的默认定义`ATLTRACE2`将使用宏和这些定义，如果你未处理 atlbase.h 之前定义这些符号。  
  
 在发布版本中`ATLTRACE2`编译为`(void) 0`。  
  
 `ATLTRACE2`限制要发送到为不能超过 1023年个字符，转储设备格式化后的字符串的内容。  
  
 **ATLTRACE**和`ATLTRACE2`具有相同的行为， **ATLTRACE**包含是为了向后兼容。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [宏](../../atl/reference/atl-macros.md)   
 [调试和错误报告全局函数](../../atl/reference/debugging-and-error-reporting-global-functions.md)
