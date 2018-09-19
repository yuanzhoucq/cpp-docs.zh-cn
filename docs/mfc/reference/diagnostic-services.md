---
title: 诊断服务 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- diagnosi [MFC]s, diagnostic services
- diagnostic macros [MFC], list of general MFC
- services [MFC], diagnostic
- MFC, diagnostic services
- general diagnostic functions and variables [MFC]
- diagnostics [MFC], diagnostic functions and variables
- diagnostics [MFC], list of general MFC
- diagnosis [MFC], diagnostic functions and variables
- diagnosis [MFC], list of general MFC
- general diagnostic macros in MFC
- diagnostic macros [MFC]
- diagnostic services [MFC]
- object diagnostic functions in MFC
- diagnostics [MFC], diagnostic services
- diagnostic functions and variables [MFC]
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14c231edc5395515836ccbbe9adea87e0f31b33d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068398"
---
# <a name="diagnostic-services"></a>诊断服务
Microsoft 基础类库提供了很多简化调试程序的诊断服务。 这些诊断服务包括宏和全局函数，让你能够跟踪程序的内存分配，在运行时转储对象的内容并打印调试消息。 诊断服务的宏和全局函数可分为以下几类：  
  
-   常规诊断宏  
  
-   常规诊断函数和变量  
  
-   对象诊断函数  
  
 这些宏和函数可用于派生自 MFC 调试和发布版本中的 `CObject` 的所有类。 但是，除 DEBUG_NEW 并验证所有不执行任何操作的发行版本中。  
  
 在调试库中，所有分配的内存块被一系列的“保护字节”包围。 如果这些字节受到错误内存写入的干扰，诊断例程可以报告问题。 如果包括行：  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 在实现文件中，所有对 **new** 的调用将存储发生内存分配的文件名和行号。 函数 [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) 将显示此附加信息，帮助你确定内存泄漏。 关于诊断输出的其他信息，另请参阅 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 类。  
  
 此外，C 运行时库还支持一组可用于调试应用程序的诊断函数。 有关详细信息，请参阅《运行时库参考》中的 [调试例程](../../c-runtime-library/debug-routines.md) 。  
  
### <a name="mfc-general-diagnostic-macros"></a>MFC 常规诊断宏  
  
|||  
|-|-|  
|[ASSERT](#assert)|打印一条消息，然后中止程序，如果指定的表达式的计算结果为 FALSE 的库的调试版本中。|  
|[ASSERT_KINDOF](#assert_kindof)|测试对象是指定类的对象还是指定类派生类的对象。|  
|[ASSERT_VALID](#assert_valid)|通过调用 `AssertValid` 成员函数测试一个对象的内部有效性；通常从 `CObject`中重写。|
|[DEBUG_NEW](#debug_new)|提供调试模式下用于所有对象分配的文件名和行号以帮助查找内存泄漏。|  
|[DEBUG_ONLY](#debug_only)|类似于 ASSERT，但不会测试表达式; 的值对于应仅在调试模式下执行的代码很有用。|  
|[请确保和 ENSURE_VALID](#ensure)|用于验证数据的正确性。|
|[THIS_FILE](#this_file)|将扩展到正在编译的文件的名称。|
|[TRACE](#trace)|在库调试版本中提供类似 `printf`的功能。|  
|[VERIFY](#verify)|类似于 ASSERT 但计算结果的调试版本的库也发行版中的表达式。|  
  
### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC 常规诊断变量和函数  
  
|||  
|-|-|  
|[afxDump](#afxdump)|将 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 信息发送给调试器输出窗口或调试终端的全局变量。|  
|[afxMemDF](#afxmemdf)|控制调试内存分配器行为的全局变量。|  
|[AfxCheckError](#afxcheckerror)|全局变量，用于测试传递的 SCODE 以查看是否出错以及如果是这样，将引发相应的错误。|  
|[AfxCheckMemory](#afxcheckmemory)|检查所有当前分配的内存的完整性。|  
|[AfxDebugBreak](#afxdebugbreak)|在执行过程中导致中断。|
|[AfxDump](#cdumpcontext_in_mfc)|如果在调试器中调用，将在调试时转储对象的状态。|  
|[AfxDump](#afxdump)|调试时转储对象的状态的内部函数。|
|[AfxDumpStack](#afxdumpstack)|生成当前堆栈的映像。 此函数始终以静态方式链接。|  
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|启用内存泄漏转储。|  
|[AfxEnableMemoryTracking](#afxenablememorytracking)|打开和关闭内存跟踪。|  
|[AfxIsMemoryBlock](#afxismemoryblock)|验证内存块是否正确分配。|  
|[AfxIsValidAddress](#afxisvalidaddress)|验证内存地址范围是否在程序边界内。|  
|[AfxIsValidString](#afxisvalidstring)|确定一个字符串指针是否有效。|  
|[AfxSetAllocHook](#afxsetallochook)|实现每次内存分配的函数调用。|  
  
### <a name="mfc-object-diagnostic-functions"></a>MFC 对象诊断函数  
  
|||  
|-|-|  
|[AfxDoForAllClasses](#afxdoforallclasses)|对支持运行时类型检查的所有 `CObject`派生类执行指定函数。|  
|[AfxDoForAllObjects](#afxdoforallobjects)|对分配 `CObject`new **的所有**派生对象执行指定函数。|  

### <a name="mfc-compilation-macros"></a>MFC 编译宏
|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS，则](#afx_secure_no_warnings)|取消显示有关对已弃用的 MFC 函数的使用的编译器警告。|  


## <a name="afx_secure_no_warnings"></a> _AFX_SECURE_NO_WARNINGS，则
取消显示有关对已弃用的 MFC 函数的使用的编译器警告。  
   
### <a name="syntax"></a>语法   
```  
_AFX_SECURE_NO_WARNINGS  
```     
### <a name="example"></a>示例  
 如果未定义 _AFX_SECURE_NO_WARNINGS，则此代码示例将产生一个编译器警告。  
  
 ```cpp
// define this before including any afx files in stdafx.h
#define _AFX_SECURE_NO_WARNINGS
```
```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a> AfxDebugBreak
调用此函数可导致中断 (对的调用位置`AfxDebugBreak`) 执行过程中的 MFC 应用程序的调试版本。  

### <a name="syntax"></a>语法    
```
void AfxDebugBreak( );    
```  
   
### <a name="remarks"></a>备注  
 `AfxDebugBreak` 在 MFC 应用程序的发布版本中不起，应删除。 此函数只应在 MFC 应用程序中。 使用 Win32 API 的版本， `DebugBreak`、 以非 MFC 应用程序中导致中断。  
   
### <a name="requirements"></a>要求  
 **标头：** afxver_.h   

##  <a name="assert"></a>  ASSERT
 其参数的计算结果。  
  
```   
ASSERT(booleanExpression)   
```  
  
### <a name="parameters"></a>参数  
 *布尔表达式*  
 指定一个表达式 （包括指针值） 的计算结果为非零值则为 0。  
  
### <a name="remarks"></a>备注  
 如果结果为 0，宏会打印诊断消息并中止程序。 如果条件为非零值，它会执行任何操作。  
  
 诊断消息具有以下形式  
  
 `assertion failed in file <name> in line <num>`  
  
 其中*名称*是源文件的名称和*num*是在源文件中失败的断言的行号。  
  
 在 MFC 的发行版，断言不计算表达式的结果，并因此不会中断该程序。 如果表达式必须计算而不考虑环境，使用 VERIFY 代替 ASSERT 宏。  
  
> [!NOTE]
>  此函数是仅在调试版本的 MFC 中可用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="assert_kindof"></a>  ASSERT_KINDOF  
 此宏断言指向的对象是指定类的一个对象或类的对象派生自指定类。  
  
```   
ASSERT_KINDOF(classname, pobject)  
```  
  
### <a name="parameters"></a>参数  
 classname  
 名称`CObject`-派生的类。  
  
 *pobject*  
 指向类对象的指针。  
  
### <a name="remarks"></a>备注  
 *Pobject*参数应是指向对象的指针，并且可以是**const**。 指向的对象和类必须支持`CObject`运行时类信息。 作为示例，以确保`pDocument`指向的对象的指针`CMyDoc`类或其派生的任何可能代码：  
  
 [!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]  
  
 使用`ASSERT_KINDOF`宏正是编码相同：  
  
 [!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]  
  
 此函数仅适用于使用声明的类 [DECLARE_DYNAMIC] (运行的时间的对象的模型-services.md #declare_dynamic 或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏。  
  
> [!NOTE]
>  此函数是仅在调试版本的 MFC 中可用。  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="assert_valid"></a>  ASSERT_VALID  
 用于测试有关的对象的内部状态有效性的假设。  
  
```   
ASSERT_VALID(pObject)   
```  
  
### <a name="parameters"></a>参数  
 *pObject*  
 指定派生自的类的对象`CObject`具有的重写版本`AssertValid`成员函数。  
  
### <a name="remarks"></a>备注  
 ASSERT_VALID 调用`AssertValid`作为其自变量传递的对象的成员函数。  
  
 在 MFC 的发行版，ASSERT_VALID 没有任何影响。 在调试版本中，它验证指针、 检查对 null 值，并调用该对象自己的`AssertValid`成员函数。 如果其中的任何测试失败，将一条警告消息显示在与相同的方式[ASSERT](#assert)。  
  
> [!NOTE]
>  此函数是仅在调试版本的 MFC 中可用。  
  
 有关详细信息和示例，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="debug_new"></a>  DEBUG_NEW  
 可查找内存泄漏的协助。  
  
```   
#define  new DEBUG_NEW   
```  
  
### <a name="remarks"></a>备注  
 DEBUG_NEW 使用一般会使用在程序中的所有位置**新**运算符将堆的存储分配。  
  
 在调试模式下 (当 **_DEBUG**定义符号)，DEBUG_NEW 跟踪的每个对象所分配的文件名和行号。 然后，使用[cmemorystate:: Dumpallobjectssince](cmemorystate-structure.md#dumpallobjectssince)成员函数使用 DEBUG_NEW 分配每个对象显示的文件名和行号分配到的位置。  
  
 若要使用 DEBUG_NEW，插入源代码文件中的以下指令：  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 无论你使用预处理器后插入此指令时，将插入 DEBUG_NEW**新**，MFC 将完成剩余。 DEBUG_NEW 编译您的程序的发行版时，解析为一个简单**新**不会生成操作，文件名和行号信息。  
  
> [!NOTE]
>  您需要在以前版本的 MFC （4.1 及更早版本） 将放`#define`调用 IMPLEMENT_DYNCREATE 或 IMPLEMENT_SERIAL 宏的所有语句之后的语句。 这不再是必需的。  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY  
 在调试模式下 (当 **_DEBUG**定义符号)，DEBUG_ONLY 计算其参数。  
  
```   
DEBUG_ONLY(expression)   
```  
  
### <a name="remarks"></a>备注  
 在发布版本中，DEBUG_ONLY 不会评估其参数。 在您将应仅在调试版本中执行的代码，这很有用。  
  
 DEBUG_ONLY 宏等同于周围*表达式*与`#ifdef _DEBUG`和`#endif`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h

 ### <a name="ensure"></a>  请确保和 ENSURE_VALID
用于验证数据的正确性。  
   
### <a name="syntax"></a>语法    
```
ENSURE(  booleanExpression )  
ENSURE_VALID( booleanExpression  )  
```
### <a name="parameters"></a>参数  
 *布尔表达式*  
 指定要测试的布尔表达式。  
   
### <a name="remarks"></a>备注  
 这些宏的目的是改进的参数验证。 宏阻止进一步处理的代码中的参数不正确。 与 ASSERT 宏，请确保宏引发除了生成断言异常。  
  
 宏的行为在两个方面，根据项目配置。 宏调用 ASSERT，然后引发一个异常，如果断言失败。 因此，在调试配置 （其中定义 _DEBUG） 宏生成断言并在发布配置中，宏生成时出现异常 （断言不会计算表达式的结果中发布配置） 异常。  
  
 该宏 ENSURE_ARG 作用类似于确保宏。  
  
 ENSURE_VALID 调用 ASSERT_VALID 宏 （这仅在调试版本中具有某种效果）。 此外，ENSURE_VALID 指针为 NULL 时引发异常。 NULL 测试工作都在调试和发布配置。  
  
 如果其中的任何测试失败，断言为相同的方式显示一条警告消息。 如果需要宏将引发无效参数异常。  
### <a name="requirements"></a>要求  
 **标头：** afx.h  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [验证](#verify)   
 [ATLENSURE](#altensure)

## <a name="this_file"></a> THIS_FILE
将扩展到正在编译的文件的名称。  
   
### <a name="syntax"></a>语法    
```
THIS_FILE    
```  
   
### <a name="remarks"></a>备注  
 使用 ASSERT 并验证宏的信息。 应用程序向导和代码向导将宏放置在他们创建的源代码文件中。  
   
### <a name="example"></a>示例  
```cpp
#ifdef _DEBUG
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif

// __FILE__ is one of the six predefined ANSI C macros that the 
// compiler recognizes. 
```
   
### <a name="requirements"></a>要求  
 **标头：** afx.h  
   
### <a name="see-also"></a>请参阅  
 [宏和全局函数](mfc-macros-and-globals.md)   
 [断言](#assert)   
 [VERIFY](#verify)


##  <a name="trace"></a>  TRACE  
 将指定的字符串发送到调试器的当前应用程序。  
  
```   
TRACE(exp)  
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)   
```  
  
### <a name="remarks"></a>备注  
 请参阅[ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2)有关跟踪的说明。 跟踪和 ATLTRACE2 具有相同的行为。  
  
 在调试版本的 MFC 中，此宏将指定的字符串发送到调试器的当前应用程序。 在发布版本中，此宏将编译为执行任何操作 （在所有生成任何代码）。  
  
 有关详细信息，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="verify"></a>  VERIFY  
 在调试版本的 MFC 中，计算其参数。  
  
```   
VERIFY(booleanExpression)   
```  
  
### <a name="parameters"></a>参数  
 *布尔表达式*  
 指定一个表达式 （包括指针值） 的计算结果为非零值则为 0。  
  
### <a name="remarks"></a>备注  
 如果结果为 0，该宏将打印诊断消息，将暂停程序。 如果条件为非零值，它会执行任何操作。  
  
 诊断消息具有以下形式  
  
 `assertion failed in file <name> in line <num>`  
  
 其中*名称*源文件的名称和*num*是在源文件中失败的断言的行号。  
  
 在发布版本的 MFC 中，验证计算表达式的值，但不打印或中断该程序。 例如，如果表达式是函数调用，将发起呼叫。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="cdumpcontext_in_mfc"></a>  afxDump (MFC 中的 CDumpContext)  
 提供了在应用程序中的基本对象转储功能。  
  
```   
CDumpContext  afxDump;   
```  
  
### <a name="remarks"></a>备注  
 `afxDump` 是预定义[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象，它使你能够发送`CDumpContext`给调试器输出窗口或调试终端的信息。 通常情况下，提供`afxDump`作为参数`CObject::Dump`。  
  
 在 Windows NT 和所有版本的 Windows，`afxDump`调试你的应用程序时，将输出发送到输出调试窗口的 Visual c + +。  
  
 仅在调试版本的 MFC 中定义此变量。 有关详细信息`afxDump`，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h


## <a name="afxdump"></a> AfxDump （内部）
MFC 使用以进行调试时转储对象的状态的内部函数。  

### <a name="syntax"></a>语法    
```
void AfxDump(const CObject* pOb);   
```
### <a name="parameters"></a>参数  
 *邮政信箱*  
 指向类的对象派生自`CObject`。  
   
### <a name="remarks"></a>备注  
 `AfxDump` 调用对象的`Dump`成员函数，并发送到的位置信息由指定`afxDump`变量。 `AfxDump` 是仅在调试版本的 MFC 中可用。  
  
 你的程序代码不应调用`AfxDump`，但应改为调用`Dump`相应对象的成员函数。  
   
### <a name="requirements"></a>要求  
 **标头：** afx.h  
   
### <a name="see-also"></a>请参阅  
 [CObject::Dump](cobject-class.md#dump)   



##  <a name="afxmemdf"></a>  afxMemDF  
 此变量从调试程序或应用程序进行访问，并可以调整分配诊断。  
  
```   
int  afxMemDF;  
```  
  
### <a name="remarks"></a>备注  
 `afxMemDF` 可以具有以下指定的枚举值`afxMemDF`:  
  
- `allocMemDF` 打开调试分配器 （在调试库中的默认设置）。  
  
- `delayFreeMemDF` 释放内存而延迟。 尽管程序释放内存块，分配器不返回到基础操作系统的内存。 这将在您的程序上放置的最大内存压力。  
  
- `checkAlwaysMemDF` 调用`AfxCheckMemory`每次分配或释放内存。 这将显著降低内存分配和释放。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="afxcheckerror"></a>  AfxCheckError  
 此函数将测试传递的 SCODE 出错。  
  
```   
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException* 
throw COleException*  
```  
  
### <a name="remarks"></a>备注  
 如果为错误，则此函数将引发异常。 如果传递的 SCODE E_OUTOFMEMORY，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)通过调用[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)。 否则，函数将引发[COleException](../../mfc/reference/coleexception-class.md)通过调用[AfxThrowOleException](exception-processing.md#afxthrowoleexception)。  
  
 此函数可用于检查调用应用程序中的 OLE 函数返回的值。 通过在您的应用程序中使用此函数测试返回值，您可使用最少的代码正确反映错误条件。  
  
> [!NOTE]
>  此函数的效果与调试生成和不调试生成的相同。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="afxcheckmemory"></a>  AfxCheckMemory  
 此函数验证可用内存池，并打印所需的错误消息。  
  
```   
BOOL  AfxCheckMemory(); 
```  
  
### <a name="return-value"></a>返回值  
 如果没有内存错误; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 如果该函数检测到没有内存损坏，会输出执行任何操作。  
  
 检查当前分配的堆上的所有内存块，包括那些由分配**新**但无法通过直接调用基础内存分配器，如分配**malloc**函数或`GlobalAlloc` Windows 函数。 如果找到任何块可能已损坏，一条消息打印到调试器输出。  
  
 如果包括行  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 在程序模块中，则后续的调用`AfxCheckMemory`分配内存时显示的文件名和行号。  
  
> [!NOTE]
>  如果您的模块中包含的可序列化类的一个或多个实现，则必须将`#define`最后一次 IMPLEMENT_SERIAL 宏调用之后的行。  
  
 此函数仅在调试版本的 MFC 中有效。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h  
 
##  <a name="afxdump"></a>  AfxDump (MFC)  
 调用此函数在调试器中进行调试时转储对象的状态。  
  
```   
void AfxDump(const CObject* pOb); 
```  
  
### <a name="parameters"></a>参数  
 *邮政信箱*  
 指向类的对象派生自`CObject`。  
  
### <a name="remarks"></a>备注  
 `AfxDump` 调用对象的`Dump`成员函数，并发送到的位置信息由指定`afxDump`变量。 `AfxDump` 是仅在调试版本的 MFC 中可用。  
  
 你的程序代码不应调用`AfxDump`，但应改为调用`Dump`相应对象的成员函数。  

### <a name="requirements"></a>要求  
 **标头：** afx.h  

### <a name="see-also"></a>请参阅  
 [CObject::Dump](cobject-class.md#dump)   


  
##  <a name="afxdumpstack"></a>  AfxDumpStack  
 此全局函数可用于生成当前堆栈的映像。  
  
```   
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT); 
```  
  
### <a name="parameters"></a>参数  
 *dwTarget*  
 指示转储输出的目标。 可能的值，可以使用按位 OR 组合 ( **&#124;**) 运算符，如下所示：  
  
- 通过 AFX_STACK_DUMP_TARGET_TRACE 发送输出[跟踪](#trace)宏。 TRACE 宏在调试版本; 仅将生成输出它在发布版本中不生成任何输出。 此外，跟踪可以重定向到调试器除了其他目标。  
  
- AFX_STACK_DUMP_TARGET_DEFAULT 发送转储输出到默认目标。 为调试版本中，输出将转到 TRACE 宏。 在发布版本中，输出会转至剪贴板。  
  
- AFX_STACK_DUMP_TARGET_CLIPBOARD 将发送到剪贴板仅输出。 是数据放置在剪贴板上以纯文本格式使用 CF_TEXT 剪贴板格式。  
  
- AFX_STACK_DUMP_TARGET_BOTH 将发送同时输出到剪贴板和 TRACE 宏。  
  
- 直接向通过 Win32 函数调试器 AFX_STACK_DUMP_TARGET_ODS 发送输出`OutputDebugString()`。 此选项将生成调试器输出在这两个调试和发行版本，调试程序附加到进程时。 AFX_STACK_DUMP_TARGET_ODS 始终达到调试器 （如果已附加），并且不能重定向。  
  
### <a name="remarks"></a>备注  
 下面的示例反映了一行调用生成的输出`AfxDumpStack`从 MFC 对话框应用程序中的按钮处理程序：  
  
```Output
=== begin AfxDumpStack output ===
00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes
0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes
0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,
unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct 
AFX_CMDHANDLE
0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes
00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes
00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned
int,long) + 312 bytes
00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned
int,unsigned int,long,long *) + 83 bytes
00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned
int,unsigned int,long) + 46 bytes
004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct
HWND__ *,unsigned int,unsigned int,long) + 237 bytes
00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned
int,unsigned int,long) + 129 bytes
BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes
BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes
=== end AfxDumpStack() output ===
```
  
 上面的输出中的每一行指示包含函数调用，并调用的函数原型的模块的完整路径名称的最后一个函数调用的地址。 如果在堆栈上的函数调用不会发生在该函数的确切地址，则显示的字节偏移量。  
  
 例如下, 表描述上面的输出的第一行：  
  
|输出|描述|  
|------------|-----------------|  
|`00427D55:`|最后一个函数调用的返回地址。|  
|`DUMP2\DEBUG\DUMP2.EXE!`|包含函数调用的模块的完整路径名称。|  
|`void AfxDumpStack(unsigned long)`|调用的函数原型。|  
|`+ 181 bytes`|以字节为单位从函数原型的地址的偏移量 (在这种情况下， `void AfxDumpStack(unsigned long)`) 到回邮地址 (在这种情况下， `00427D55`)。|  
  
 `AfxDumpStack` 现已推出调试和非调试版本的 MFC 库;但是，即使可执行文件在共享 DLL 中使用 MFC 的函数是始终以静态方式，链接。 在共享库实现中，MFCS42 中找到了该函数。LIB 库 （和及其变体）。  
  
 若要成功使用此函数：  
  
-   该文件了内部错误。DLL 必须位于你的路径。 如果您不具备此 DLL，该函数将显示一条错误消息。 请参阅[图像帮助库](/windows/desktop/Debug/image-help-library)上提供了内部错误的函数集的信息。  
  
-   对堆栈帧的模块必须包含调试信息。 如果它们不包含调试信息，该函数仍将生成堆栈跟踪，但将不详细跟踪。  
### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="afxenablememoryleakdump"></a>  AfxEnableMemoryLeakDump  
 启用和禁用内存泄漏转储 AFX_DEBUG_STATE 析构函数中。  
  
```  
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```  
  
### <a name="parameters"></a>参数  
*bDump*<br/>
[in]TRUE 表示已启用内存泄漏转储;FALSE 表示已禁用内存泄漏转储。  
  
### <a name="return-value"></a>返回值  
 此标志的上一个值。  
  
### <a name="remarks"></a>备注  
 当应用程序卸载 MFC 库时，MFC 库将检查内存泄漏。 现在，通过向用户报告任何内存泄露**调试**Visual Studio 窗口。  
  
 如果应用程序在加载 MFC 库之前加载另一个库，则会将该库中的一些内存分配误报为内存泄漏。 MFC 库报告错误的内存泄漏时，这些误报可能导致应用程序缓慢关闭。 在这种情况下，使用 `AfxEnableMemoryLeakDump` 禁用内存泄漏转储。  
  
> [!NOTE]
>  如果使用此方法来关闭内存泄漏转储，将不会在应用程序中收到有效内存泄漏的报告。 只有确信内存泄漏报告中包含误报时才使用此方法。  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="afxenablememorytracking"></a>  AfxEnableMemoryTracking  
 在 MFC 的调试版本中正常情况下启用诊断内存跟踪。  
  
```   
BOOL AfxEnableMemoryTracking(BOOL bTrack); 
```  
  
### <a name="parameters"></a>参数  
 *bTrack*  
 将此值设置为 TRUE 将在内存跟踪;FALSE 会将其关闭。  
  
### <a name="return-value"></a>返回值  
 启用跟踪标志的以前的设置。  
  
### <a name="remarks"></a>备注  
 使用此函数禁用跟踪在知道正确分配块的代码的部分。  
  
 有关详细信息`AfxEnableMemoryTracking`，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。  
  
> [!NOTE]
>  此函数仅在调试版本的 MFC 中有效。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]  
  
### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="afxismemoryblock"></a>  AfxIsMemoryBlock  
 测试以确保它表示当前处于活动状态的内存块的诊断版本已分配的内存地址**新**。  
  
```   
BOOL AfxIsMemoryBlock(
    const void* p,  
    UINT nBytes,  
    LONG* plRequestNumber = NULL); 
```  
  
### <a name="parameters"></a>参数  
 *p*  
 指向要测试的内存块。  
  
 *nBytes*  
 包含以字节为单位的内存块的长度。  
  
 *plRequestNumber*  
 指向**长**将填充内存块分配序列号，或如果它不表示当前处于活动状态的内存块，则零的整数。  
  
### <a name="return-value"></a>返回值  
 当前分配的内存块，且长度为正确的; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 它还检查原始分配的大小根据指定的大小。 如果该函数将返回非零值，以返回分配序列号*plRequestNumber*。 此数字表示相对于所有其他分配块时的顺序**新**分配。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]  
  
### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="afxisvalidaddress"></a>  AfxIsValidAddress  
 测试以确保包含完全在程序的内存空间内任何内存地址。  
  
```   
BOOL AfxIsValidAddress(
    const void* lp,  
    UINT nBytes,  
    BOOL bReadWrite = TRUE); 
```  
  
### <a name="parameters"></a>参数  
 *lp*  
 指向要测试的内存地址。  
  
 *nBytes*  
 包含要进行测试的内存字节数。  
  
 *bReadWrite*  
 指定的内存是同时用于读取和写入 (TRUE) 或只需读取 (FALSE)。  
  
### <a name="return-value"></a>返回值  
 在调试版本中，如果在指定的内存块，非零值被包含完全在程序的内存空间中;否则为 0。  
  
 在非调试版本中，如果非零*lp*不为 NULL，否则为 0。  
  
### <a name="remarks"></a>备注  
 该地址并不局限于由分配块**新**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]  
  
### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="afxisvalidstring"></a>  AfxIsValidString  
 使用此函数来确定为字符串的指针是否有效。  
  
```   
BOOL  AfxIsValidString(
    LPCSTR lpsz,  
    int nLength = -1); 
```  
  
### <a name="parameters"></a>参数  
 *lpsz*  
 要测试的指针。  
  
 *nLength*  
 指定要进行测试，以字节为单位的字符串的长度。 值为-1 指示该字符串将以 null 结尾。  
  
### <a name="return-value"></a>返回值  
 在调试版本中，如果指定的指针指向为字符串指定的大小; 的非零值否则为 0。  
  
 在非调试版本中，如果非零*lpsz*不为 NULL，否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="afxsetallochook"></a>  AfxSetAllocHook  
 设置允许指定函数的调用之前每个内存块分配的挂钩。  
  
```   
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook); 
```  
  
### <a name="parameters"></a>参数  
 *pfnAllocHook*  
 指定要调用的函数的名称。 请参阅分配函数的原型的备注部分。  
  
### <a name="return-value"></a>返回值  
 如果你想要允许分配; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 Microsoft 基础类库调试内存分配器可以调用用户定义的挂钩函数，以允许用户监视内存分配并控制是否允许分配。 分配挂钩函数原型如下所示：  
  
 **BOOL AFXAPI AllocHook (size_t** `nSize` **，BOOL** `bObject`**很长** `lRequestNumber` **);**  
  
 *nSize*  
 建议的内存分配的大小。  
  
 *bObject*  
 如果分配长度为 TRUE `CObject`-派生的对象; 否则为 FALSE。  
  
 *lRequestNumber*  
 内存分配序列号。  
  
 请注意，调用约定 AFXAPI 意味着被调用方必须从堆栈移除参数。  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="afxdoforallclasses"></a>  AfxDoForAllClasses  
 调用指定的迭代函数的所有可序列化`CObject`-应用程序的内存空间中派生类。  
  
```   
void  
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>参数  
 *pfn*  
 指向迭代函数要调用的每个类。 函数自变量是一个指向`CRuntimeClass`对象和函数的调用方提供的额外数据的 void 指针。  
  
 *pContext*  
 指向调用方可以提供对迭代函数的可选数据。 此指针可以为 NULL。  
  
### <a name="remarks"></a>备注  
 可序列化`CObject`的派生的类是使用 DECLARE_SERIAL 宏派生的类。 将指针传递给`AfxDoForAllClasses`中*pContext*传递给指定的迭代函数每次调用它。  
  
> [!NOTE]
>  此函数仅在调试版本的 MFC 中有效。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]  
  
### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="afxdoforallobjects"></a>  AfxDoForAllObjects  
 执行指定的迭代函数，用于所有对象都派生自`CObject`与分配**新**。  
  
```   
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>参数  
 *pfn*  
 指向要为每个对象执行的迭代函数。 函数自变量是一个指向`CObject`和 void 指针到函数的调用方提供的额外数据。  
  
 *pContext*  
 指向调用方可以提供对迭代函数的可选数据。 此指针可以为 NULL。  
  
### <a name="remarks"></a>备注  
 不会枚举堆栈，全局或嵌入的对象。 将指针传递给`AfxDoForAllObjects`中*pContext*传递给指定的迭代函数每次调用它。  
  
> [!NOTE]
>  此函数仅在调试版本的 MFC 中有效。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)