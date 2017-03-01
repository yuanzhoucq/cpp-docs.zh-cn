---
title: "调试和错误报告的宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
caps.latest.revision: 18
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
ms.openlocfilehash: 112b43c325d4b73d2cc15ba41d9aac255c74da8a
ms.lasthandoff: 02/24/2017

---
# <a name="debugging-and-error-reporting-macros"></a>调试和错误报告的宏
这些宏提供有用的调试和跟踪工具。  
  
|||  
|-|-|  
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|将写入输出窗口中，任何界面泄漏时检测到`_Module.Term`调用。|  
|[_ATL_DEBUG_QI](#_atl_debug_qi)|写入到的所有调用`QueryInterface`到输出窗口。|  
|[ATLASSERT](#atlassert)|执行与相同的功能[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)宏在 C 运行库中找到。|  
|[ATLENSURE](#atlensure)|执行参数验证。 调用`AtlThrow`如果需要|  
|[ATLTRACENOTIMPL](#atltracenotimpl)|将一条消息发送到转储设备未实现指定的函数。|  
|[ATLTRACE](http://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e)|写入输出设备，例如调试器窗口中，按照指定的标志和水平报告警告。 包括的向后兼容性。|  
|[ATLTRACE2](#atltrace2)|写入输出设备，例如调试器窗口中，按照指定的标志和水平报告警告。|  
  
##  <a name="a-nameatldebuginterfacesa--atldebuginterfaces"></a><a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES  
 在包含任何要跟踪所有的 ATL 标头文件之前定义此宏`AddRef`和**版本**调用组件的接口连接到输出窗口上。  
  
```
#define _ATL_DEBUG_INTERFACES
```  
  
### <a name="remarks"></a>备注  
 跟踪输出将显示如下所示︰  
  
 `ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`  
  
 每个跟踪的第一部分将始终为`ATL: QIThunk`。 接下来是一个值，标识特定*接口转换 （thunk）*正在使用。 接口转换 （thunk） 是用于维护的引用计数并提供在此处使用的跟踪功能的对象。 在每次调用创建一个新的接口 thunk`QueryInterface`除外征求**IUnknown**接口 （在这种情况下，相同的转换 （thunk） 返回每次以符合 COM 的一致性规则）。  
  
 接下来您将看到`AddRef`或**版本**，该值指示调用了哪个方法。 接下来，您将看到一个标识其接口引用计数已更改的对象的值。 跟踪的值是**这**对象的指针。  
  
 此外，跟踪的引用计数是后该转换 （thunk） 的引用计数`AddRef`或**版本**调用。 请注意，此引用计数可能会与该对象的引用计数不匹配。 每个转换 （thunk） 保留其自身的引用计数来帮助您完全符合 COM 的引用计数规则。  
  
 跟踪的信息的最后部分是对象和所影响的接口的名称`AddRef`或**版本**调用。  
  
 当服务器关闭时检测到泄漏的任何接口和`_Module.Term`调用将会记录如下︰  
  
 `ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`  
  
 直接映射到以前的跟踪语句中提供的信息在此处提供的信息，以便你可以检查的引用计数在整个界面转换 （thunk） 的整个生存期。 此外，在该界面转换 （thunk） 上获取相对值的指示最大引用数。  
  
> [!NOTE]
> `_ATL_DEBUG_INTERFACES`可在零售版本。  
  
##  <a name="a-nameatldebugqia--atldebugqi"></a><a name="_atl_debug_qi"></a>_ATL_DEBUG_QI  
 写入到的所有调用`QueryInterface`到输出窗口。  
  
```
#define _ATL_DEBUG_QI
```  
  
### <a name="remarks"></a>备注  
 如果调用`QueryInterface`失败，将显示输出窗口︰  
  
 *接口名称* - `failed`  
  
##  <a name="a-nameatlasserta--atlassert"></a><a name="atlassert"></a>ATLASSERT  
 `ATLASSERT`宏执行相同的功能[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)宏在 C 运行库中找到。  
  
```
ATLASSERT(booleanExpression);
```  
  
### <a name="parameters"></a>参数  
 `booleanExpression`  
 计算结果为零或不为零的表达式（包括指针）。  
  
### <a name="remarks"></a>备注  
 在调试版本中`ATLASSERT`计算`booleanExpression`并在结果为 false 时生成调试报告。  

## <a name="requirements"></a>要求  
 **标头︰** atldef.h  
    
##  <a name="a-nameatlensurea--atlensure"></a><a name="atlensure"></a>ATLENSURE  
 使用此宏来验证传递给函数的参数。  
  
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
 这些宏提供了一种机制来检测和通知不正确的参数用法的用户。  
  
 宏调用`ATLASSERT`并且当条件失败时调用`AtlThrow`。  
  
 在**ATLENSURE**的情况下，`AtlThrow`称为 E_FAIL。  
  
 在**ATLENSURE_THROW**的情况下，`AtlThrow`调用使用指定的 HRESULT。  
  
 之间的差异**ATLENSURE**和`ATLASSERT`在于**ATLENSURE**发行版中的异常以及生成如下所示的调试版本，则会引发。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&108;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]  

## <a name="requirements"></a>要求  
 **标头：** afx.h  

##  <a name="a-nameatltracenotimpla--atltracenotimpl"></a><a name="atltracenotimpl"></a>ATLTRACENOTIMPL  
 ATL 的调试版本中发送字符串"`funcname`未实现"到转储设备并返回**E_NOTIMPL**。  
  
```
ATLTRACENOTIMPL(funcname);
```  
  
### <a name="parameters"></a>参数  
 `funcname`  
 [in]包含未实现的函数名称的字符串。  
  
### <a name="remarks"></a>备注  
 在发布版本中，只需返回**E_NOTIMPL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&127;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头︰** atltrace.h 

##  <a name="a-nameatla--atltrace"></a><a name="atl_"></a>ATLTRACE
 写入输出设备，例如调试器窗口中，按照指定的标志和水平报告警告。 包括的向后兼容性。  
  
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
 [in]事件或在其上的方法来报告的类型。 请参阅有关类别的列表备注。  
  
 `level`  
 [in]对报表的跟踪级别。 请参阅有关的详细信息备注。  
  
 `lpszFormat`  
 [in]要发送到转储设备的格式化的字符串。  
  
### <a name="remarks"></a>备注  
 请参阅[ATLTRACE2](#atltrace2)有关的说明**ATLTRACE**。 **ATLTRACE**和`ATLTRACE2`具有相同的行为， **ATLTRACE**是为了向后兼容。  
  
##  <a name="a-nameatltrace2a--atltrace2"></a><a name="atltrace2"></a>ATLTRACE2  
 写入输出设备，例如调试器窗口中，按照指定的标志和水平报告警告。  
  
```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```  
  
### <a name="parameters"></a>参数  
 `exp`  
 [in]要将发送到 Visual c + + 输出窗口或捕获这些消息的任何应用程序的字符串。  
  
 `category`  
 [in]事件或在其上的方法来报告的类型。 请参阅有关类别的列表备注。  
  
 `level`  
 [in]对报表的跟踪级别。 请参阅有关的详细信息备注。  
  
 `lpszFormat`  
 [in]`printf`-样式格式字符串，用于创建要发送到转储设备的字符串。  
  
### <a name="remarks"></a>备注  
 缩写形式`ATLTRACE2`写入到调试器的字符串的输出窗口。 第二种形式的`ATLTRACE2`还将输出写入到调试器的输出窗口中，但可能会发生 ATL/MFC 跟踪工具的设置 (请参阅[ATLTraceTool 示例](../../visual-cpp-samples.md))。 例如，如果您设置`level`4 和 ATL/MFC 跟踪工具到级别为 0，则将看不该消息。 *级别*可以是 0、 1、 2、 3 或 4。 默认情况下，0，将进行相应报告最严重的问题。  
  
 `category`参数列出要设置的跟踪标志。 这些标志对应于为其要报告的方法的类型。 下表列出可用于有效的跟踪标志`category`参数。  
  
### <a name="atl-trace-flags"></a>ATL 跟踪标志  
  
|ATL 类别|说明|  
|------------------|-----------------|  
|`atlTraceGeneral`|有关 ATL 的所有应用程序的报告。 默认值。|  
|`atlTraceCOM`|COM 方法的报表。|  
|`atlTraceQI`|QueryInterface 调用的报表。|  
|`atlTraceRegistrar`|此注册对象的报表。|  
|`atlTraceRefcount`|更改引用计数的报表。|  
|`atlTraceWindowing`|有关 windows 方法; 这些方法的报告例如，将报告一个无效的消息映射 id。|  
|`atlTraceControls`|在控件; 上的报表例如，报告时销毁控件或它的窗口。|  
|`atlTraceHosting`|报表承载消息;例如，将报告激活一个容器中的客户端时。|  
|`atlTraceDBClient`|有关 OLE DB 使用者模板; 报告例如，当调用 GetData 失败时，输出可以包含相应的 HRESULT。|  
|`atlTraceDBProvider`|有关 OLE DB 提供程序模板; 报告例如，报告如果某一列创建失败。|  
|`atlTraceSnapin`|MMC 管理单元应用程序的报表。|  
|`atlTraceNotImpl`|未实现所指示的函数的报表。|  
|**atlTraceAllocation**|报表打印 atldbgmem.h 中的调试工具的内存的消息。|  
  
### <a name="mfc-trace-flags"></a>MFC 跟踪标志  
  
|MFC 类别|说明|  
|------------------|-----------------|  
|**traceAppMsg**|通用，MFC 消息。 始终建议。|  
|**traceDumpContext**|从消息[CDumpContext](../../mfc/reference/cdumpcontext-class.md)。|  
|**traceWinMsg**|MFC 的消息处理代码中的消息。|  
|**traceMemory**|MFC 的内存管理代码中的消息。|  
|**traceCmdRouting**|来自 MFC 的窗口的消息的命令路由的代码。|  
|**traceHtml**|从 MFC 的 DHTML 对话框支持消息。|  
|**traceSocket**|从 MFC 的套接字支持消息。|  
|**traceOle**|从 MFC 的 OLE 支持的消息。|  
|**traceDatabase**|从 MFC 的数据库支持的消息。|  
|**traceInternet**|从 MFC 的 Internet 支持的消息。|  
  
 若要声明一个自定义跟踪类别，声明的全局实例`CTraceCategory`类，如下所示︰  
  
 [!code-cpp[NVC_ATL_Utilities #&109;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]  
  
 类别名称，`MY_CATEGORY`在本示例中，是对指定的名称`category`参数。 第一个参数是会在 ATL/MFC 跟踪工具中显示的类别名称。 第二个参数是默认跟踪级别。 此参数是可选的并且默认跟踪级别为 0。  
  
 若要使用用户定义的类别︰  
  
 [!code-cpp[NVC_ATL_Utilities #&110;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]  
  
 若要指定您要筛选跟踪消息，插入这些宏的定义，则在之前的 Stdafx.h`#include <atlbase.h>`语句。  
  
 或者，可以设置筛选器中的预处理器指令中**属性页**对话框。 单击**预处理器**选项卡上，然后插入到全局**预处理器定义**编辑框。  
  
 Atlbase.h 包含的默认定义`ATLTRACE2`将使用宏，并且这些定义，如果处理 atlbase.h 之前，未定义这些符号。  
  
 在发布生成`ATLTRACE2`编译为`(void) 0`。  
  
 `ATLTRACE2`限制要设置格式后将发送到转储设备数不能超过 1023年个字符的字符串的内容。  
  
 **ATLTRACE**和`ATLTRACE2`具有相同的行为， **ATLTRACE**是为了向后兼容。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities #&111;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)   
 [调试和错误报告的全局函数](../../atl/reference/debugging-and-error-reporting-global-functions.md)

