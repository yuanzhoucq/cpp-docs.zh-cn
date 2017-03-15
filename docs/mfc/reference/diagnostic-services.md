---
title: "诊断服务 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- diagnosis, diagnostic services
- diagnostic macros, list of general MFC
- services, diagnostic
- MFC, diagnostic services
- general diagnostic functions and variables
- diagnostics, diagnostic functions and variables
- diagnostics, list of general MFC
- diagnosis, diagnostic functions and variables
- diagnosis, list of general MFC
- general diagnostic macros in MFC
- diagnostic macros
- diagnostic services
- object diagnostic functions in MFC
- diagnostics, diagnostic services
- diagnostic functions and variables
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 86fe366a4d7863fb9339b7b5a9f880103876de33
ms.lasthandoff: 02/24/2017

---
# <a name="diagnostic-services"></a>诊断服务
Microsoft 基础类库提供了很多简化调试程序的诊断服务。 这些诊断服务包括宏和全局函数，让你能够跟踪程序的内存分配，在运行时转储对象的内容并打印调试消息。 诊断服务的宏和全局函数可分为以下几类：  
  
-   常规诊断宏  
  
-   常规诊断函数和变量  
  
-   对象诊断函数  
  
 这些宏和函数了可用于所有类都派生自此`CObject`在 MFC 的调试和发布的版本。 但是，除`DEBUG_NEW`和**验证**不执行任何操作的发布版本中。  
  
 在调试库中，所有分配的内存块被一系列的“保护字节”包围。 如果这些字节受到错误内存写入的干扰，诊断例程可以报告问题。 如果包括行：  
  
 [!code-cpp[NVC_MFCCObjectSample #&14;](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 在实现文件中，所有调用**新**将存储发生内存分配的文件名和行号。 该函数[CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince)将显示这一额外信息，从而可以确定内存泄漏。 另请参阅到类[CDumpContext](../../mfc/reference/cdumpcontext-class.md)诊断输出上的其他信息。  
  
 此外，C 运行时库还支持一组可用于调试应用程序的诊断函数。 有关详细信息，请参阅[调试例程](../../c-runtime-library/debug-routines.md)运行时库参考中。  
  
### <a name="mfc-general-diagnostic-macros"></a>MFC 常规诊断宏  
  
|||  
|-|-|  
|[断言](#assert)|打印一条消息，然后中止程序，如果指定的表达式的计算结果为**FALSE**库的调试版本中。|  
|[ASSERT_KINDOF](#assert_kindof)|测试对象是指定类的对象还是指定类派生类的对象。|  
|[ASSERT_VALID](#assert_valid)|测试一个对象的内部有效性通过调用其`AssertValid`成员函数; 通常重写从`CObject`。|  
|[DEBUG_NEW](#debug_new)|提供调试模式下用于所有对象分配的文件名和行号以帮助查找内存泄漏。|  
|[DEBUG_ONLY](#debug_only)|类似于**ASSERT**但不会测试表达式; 的值的应仅在调试模式下执行的代码很有用。|  
|[TRACE](#trace)|提供了`printf`-喜欢库的调试版本中的功能。|  
|[验证](#verify)|类似于**ASSERT** ，但是计算库以及如下所示的调试版本的发行版中的表达式。|  
  
### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC 常规诊断变量和函数  
  
|||  
|-|-|  
|[afxDump](#afxdump)|将发送的全局变量[CDumpContext](../../mfc/reference/cdumpcontext-class.md)向调试器输出窗口或调试终端的信息。|  
|[afxMemDF](#afxmemdf)|控制调试内存分配器行为的全局变量。|  
|[AfxCheckError](#afxcheckerror)|用来测试传入的全局变量**SCODE**若要查看是否它是一个错误并且，如果是这样，将引发相应的错误。|  
|[AfxCheckMemory](#afxcheckmemory)|检查所有当前分配的内存的完整性。|  
|[AfxDump](#cdumpcontext_in_mfc_)|如果在调试器中调用，将在调试时转储对象的状态。|  
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
|[AfxDoForAllClasses](#afxdoforallclasses)|对所有执行指定的函数`CObject`-派生的类支持运行时类型检查。|  
|[AfxDoForAllObjects](#afxdoforallobjects)|对所有执行指定的函数`CObject`-派生的对象分配了与**新**。|  
  
##  <a name="a-nameasserta--assert"></a><a name="assert"></a>断言
 该方法的参数的计算结果。  
  
```   
ASSERT(booleanExpression)   
```  
  
### <a name="parameters"></a>参数  
 `booleanExpression`  
 指定一个计算结果为非零或不为零的表达式 （包括指针值）。  
  
### <a name="remarks"></a>备注  
 如果结果为 0，该宏将打印诊断消息并中止程序。 如果该条件不为零，则毫无用处。  
  
 诊断消息具有以下形式  
  
 `assertion failed in file <name> in line <num>`  
  
 其中*名称*的源文件的名称和*num*是在源文件中失败的断言的行号。  
  
 在发行版的 MFC 中， **ASSERT**不计算表达式，并因此不会中断该程序。 无论环境如何，必须对表达式进行计算，如果使用**验证**宏代替了**ASSERT**。  
  
> [!NOTE]
>  此函数是仅在调试版的 MFC 中可用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&44;](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameassertkindofa--assertkindof"></a><a name="assert_kindof"></a>ASSERT_KINDOF  
 此宏断言指向的对象是指定类的对象或从指定的类派生一个类的对象。  
  
```   
ASSERT_KINDOF(classname, pobject)  
```  
  
### <a name="parameters"></a>参数  
 *类名*  
 名称`CObject`的派生类。  
  
 *pobject*  
 指向类对象的指针。  
  
### <a name="remarks"></a>备注  
 *Pobject*参数应该是指针指向的对象，并且可以为**const**。 指向的对象并且该类必须支持`CObject`运行时类信息。 作为示例，以确保`pDocument`是指向的对象的指针`CMyDoc`类，或任何其衍生产品，您可以编写代码︰  
  
 [!code-cpp[NVC_MFCDocView #&194;](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]  
  
 使用`ASSERT_KINDOF`宏是完全相同的编码︰  
  
 [!code-cpp[NVC_MFCDocView #&195;](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]  
  
 此函数仅适用于与声明的类 [DECLARE_DYNAMIC] (运行的时间的对象的模型-services.md #declare_dynamic 或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏。  
  
> [!NOTE]
>  此函数是仅在调试版的 MFC 中可用。  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameassertvalida--assertvalid"></a><a name="assert_valid"></a>ASSERT_VALID  
 用于测试有关的对象的内部状态的有效性的假设。  
  
```   
ASSERT_VALID(pObject)   
```  
  
### <a name="parameters"></a>参数  
 `pObject`  
 指定派生自的类的对象`CObject`具有的重写版本`AssertValid`成员函数。  
  
### <a name="remarks"></a>备注  
 `ASSERT_VALID`调用`AssertValid`作为其参数传递的对象的成员函数。  
  
 在发行版的 MFC 中，`ASSERT_VALID`不执行任何操作。 在调试版本中，它验证指针，根据检查**NULL**，并调用该对象自己的`AssertValid`成员函数。 如果上述任何测试失败，将一条警告消息显示在相同的方式[ASSERT](#assert)。  
  
> [!NOTE]
>  此函数是仅在调试版的 MFC 中可用。  
  
 有关详细信息和示例，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample #&19;](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="a-namedebugnewa--debugnew"></a><a name="debug_new"></a>DEBUG_NEW  
 帮助中查找内存泄漏。  
  
```   
#define  new DEBUG_NEW   
```  
  
### <a name="remarks"></a>备注  
 您可以使用`DEBUG_NEW`您一般会使用的程序中无处不在**新**运算符来分配堆存储。  
  
 在调试模式下 (当**_DEBUG**定义符号)，`DEBUG_NEW`跟踪的每个对象所分配的文件名和行号。 然后，使用[CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince)用的成员函数，每个对象分配`DEBUG_NEW`随后将显示的文件名和行号以及分配到何处。  
  
 若要使用`DEBUG_NEW`，您的源文件中插入以下指令︰  
  
 [!code-cpp[NVC_MFCCObjectSample #&14;](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 插入此指令后，将插入预处理器`DEBUG_NEW`任何位置使用**新**，和 MFC 会完成其余操作。 当编译您的程序的发行版`DEBUG_NEW`解析为一个简单**新**不会生成操作中，文件名和行号信息。  
  
> [!NOTE]
>  您需要在以前版本的 MFC （4.1 及更早版本） 将放`#define`后调用的所有语句语句`IMPLEMENT_DYNCREATE`或`IMPLEMENT_SERIAL`宏。 这不再是必需的。  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="a-namedebugonlya--debugonly"></a><a name="debug_only"></a>DEBUG_ONLY  
 在调试模式下 (当**_DEBUG**定义符号)，`DEBUG_ONLY`其参数的计算结果。  
  
```   
DEBUG_ONLY(expression)   
```  
  
### <a name="remarks"></a>备注  
 在发布版本中， **DEBUG_ONLY**不会评估其参数。 应仅在调试版本中执行的代码时，这非常有用。  
  
 `DEBUG_ONLY`宏等效于周围*表达式*与**#ifdef _DEBUG**和`#endif`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&32;](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="a-nametracea--trace"></a><a name="trace"></a>跟踪  
 将指定的字符串发送到调试器当前应用程序。  
  
```   
TRACE(exp)  
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)   
```  
  
### <a name="remarks"></a>备注  
 请参阅[ATLTRACE2](http://msdn.microsoft.com/library/467ff555-e7a5-4f94-bdd9-50ee27ab9986)有关的说明**跟踪**。 **跟踪**和`ATLTRACE2`具有相同的行为。  
  
 在 MFC 的调试版本中，该宏将指定的字符串发送到调试器当前应用程序。 在发布版本中，此宏编译为执行任何操作 （在所有生成任何代码）。  
  
 有关详细信息，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="a-nameverifya--verify"></a><a name="verify"></a>验证  
 在 MFC 的调试版本，计算结果其参数。  
  
```   
VERIFY(booleanExpression)   
```  
  
### <a name="parameters"></a>参数  
 `booleanExpression`  
 指定一个计算结果为非零或不为零的表达式 （包括指针值）。  
  
### <a name="remarks"></a>备注  
 如果结果为 0，宏将打印诊断消息并中止程序。 如果该条件不为零，则毫无用处。  
  
 诊断消息具有以下形式  
  
 `assertion failed in file <name> in line <num>`  
  
 其中*名称*是源文件的名称和*num*是在源文件中失败的断言的行号。  
  
 在发行版的 MFC 中，**验证**计算表达式的值，但不打印或中断该程序。 例如，如果表达式是函数调用，则发起呼叫。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&198;](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="a-namecdumpcontextinmfca--afxdump-cdumpcontext-in-mfc"></a><a name="cdumpcontext_in_mfc_"></a>afxDump (MFC 中的 CDumpContext)  
 提供了应用程序中的基本对象转储功能。  
  
```   
CDumpContext  afxDump;   
```  
  
### <a name="remarks"></a>备注  
 `afxDump`是一个预定义[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象，它使您能够将发送`CDumpContext`向调试器输出窗口或调试终端的信息。 通常情况下，提供`afxDump`以参数形式向`CObject::Dump`。  
  
 在 Windows NT 和所有版本的 Windows，`afxDump`调试您的应用程序时，将输出发送到 Visual c + + 的输出调试窗口。  
  
 仅在 MFC 的调试版本中定义此变量。 有关详细信息`afxDump`，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities 第&23;](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="a-nameafxmemdfa--afxmemdf"></a><a name="afxmemdf"></a>afxMemDF  
 此变量可从调试器或程序进行访问，也可以调整分配诊断。  
  
```   
int  afxMemDF;  
```  
  
### <a name="remarks"></a>备注  
 `afxMemDF`可以具有下列值以指定由枚举`afxMemDF`:  
  
- **allocMemDF**打开调试分配器 （在调试库中的默认设置）。  
  
- **delayFreeMemDF**延迟释放内存。 您的程序释放内存块，而分配器不返回到基础操作系统的内存。 这将在您的程序上放置的最大内存压力。  
  
- **checkAlwaysMemDF**调用`AfxCheckMemory`每次分配或释放内存。 这将显著降低内存分配和释放。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&30;](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="a-nameafxcheckerrora--afxcheckerror"></a><a name="afxcheckerror"></a>AfxCheckError  
 此函数将测试传递**SCODE**以查看它是否是错误。  
  
```   
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException* 
throw COleException*  
```  
  
### <a name="remarks"></a>备注  
 如果为错误，则此函数将引发异常。 如果传入`SCODE`是**E_OUTOFMEMORY**，该函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)通过调用[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)。 否则，该函数将引发[COleException](../../mfc/reference/coleexception-class.md)通过调用[AfxThrowOleException](exception-processing.md#afxthrowoleexception)。  
  
 此函数可用于检查调用应用程序中的 OLE 函数返回的值。 通过在您的应用程序中使用此函数测试返回值，您可使用最少的代码正确反映错误条件。  
  
> [!NOTE]
>  此函数的效果与调试生成和不调试生成的相同。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer 第&33;](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h

##  <a name="a-nameafxcheckmemorya--afxcheckmemory"></a><a name="afxcheckmemory"></a>AfxCheckMemory  
 此函数验证可用内存池，并输出所需的错误消息。  
  
```   
BOOL  AfxCheckMemory(); 
```  
  
### <a name="return-value"></a>返回值  
 如果没有内存错误; 则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 如果该函数检测到没有内存损坏，它将输出执行任何操作。  
  
 检查堆上当前分配的所有内存块，包括那些由分配**新**但无法通过直接调用基础内存分配器，如分配`malloc`函数或**GlobalAlloc** Windows 函数。 如果找到任何块可能已损坏，则会将一条消息打印到调试程序输出。  
  
 如果包括行  
  
 [!code-cpp[NVC_MFCCObjectSample #&14;](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 在程序模块中，则后续的调用`AfxCheckMemory`分配内存时显示的文件名和行号。  
  
> [!NOTE]
>  如果您的模块中包含的可序列化类的一个或多个实现，则必须先将`#define`后的最后一个行`IMPLEMENT_SERIAL`宏调用。  
  
 此函数仅在 MFC 的调试版本中起作用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCObjectSample #&26;](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h  
 
##  <a name="a-namemfca--afxdump-mfc"></a><a name="mfc_"></a>AfxDump (MFC)  
 调用此函数在调试器在调试时转储对象的状态。  
  
```   
void AfxDump(const CObject* pOb); 
```  
  
### <a name="parameters"></a>参数  
 `pOb`  
 指向类的对象的指针派生自`CObject`。  
  
### <a name="remarks"></a>备注  
 **AfxDump**调用对象的`Dump`成员函数，并发送到的位置信息由指定`afxDump`变量。 **AfxDump**仅在调试版的 MFC 中可用。  
  
 您的程序代码不应调用**AfxDump**，但应改为调用`Dump`成员函数的适当的对象。  
  
##  <a name="a-nameafxdumpstacka--afxdumpstack"></a><a name="afxdumpstack"></a>AfxDumpStack  
 此全局函数可以用于生成在当前堆栈的图像。  
  
```   
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT); 
```  
  
### <a name="parameters"></a>参数  
 *dwTarget*  
 指示转储输出的目标。 可能的值，可以使用按位 OR 组合 ( **|**) 运算符，如下所示︰  
  
- **AFX_STACK_DUMP_TARGET_TRACE**将输出通过发送[跟踪](#trace)宏。 **跟踪**宏生成输出中仅在调试版本; 它在发布版本中不生成任何输出。 此外，**跟踪**可以重定向到除调试器外的其他目标。  
  
- **AFX_STACK_DUMP_TARGET_DEFAULT**发送转储输出到默认目标。 为调试版本中，输出将转到**跟踪**宏。 在发布版本中，输出会转至剪贴板中。  
  
- **AFX_STACK_DUMP_TARGET_CLIPBOARD**将输出发送到仅剪贴板。 的数据放在为纯文本使用剪贴板**CF_TEXT**剪贴板格式。  
  
- **AFX_STACK_DUMP_TARGET_BOTH**将输出到剪贴板和发送**跟踪**宏，同时。  
  
- **AFX_STACK_DUMP_TARGET_ODS**输出将直接发送到调试器的 Win32 函数通过**OutputDebugString()**。 此选项将在这两个调试生成调试程序输出和发行版本时将调试器附加到进程。 **AFX_STACK_DUMP_TARGET_ODS**总是到达调试器 （如果它附加的），并且不能重定向。  
  
### <a name="remarks"></a>备注  
 下面的示例反映从调用生成的输出一行`AfxDumpStack`从 MFC 对话框应用程序中的一个按钮处理程序︰  
  
 `=== begin AfxDumpStack output ===`  
  
 `00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes`  
  
 `0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes`  
  
 `0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,`  
  
 `unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct AFX_CMDHANDLE`  
  
 `0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned`  
  
 `int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes`  
  
 `00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned`  
  
 `int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes`  
  
 `00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned`  
  
 `int,long) + 312 bytes`  
  
 `00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned`  
  
 `int,unsigned int,long,long *) + 83 bytes`  
  
 `00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned`  
  
 `int,unsigned int,long) + 46 bytes`  
  
 `004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct`  
  
 `HWND__ *,unsigned int,unsigned int,long) + 237 bytes`  
  
 `00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned`  
  
 `int,unsigned int,long) + 129 bytes`  
  
 `BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes`  
  
 `BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes`  
  
 `=== end AfxDumpStack() output ===`  
  
 上面的输出中的每一行指示最后一个函数调用，包含函数调用，并调用的函数原型的模块的完整路径名称的地址。 如果在该函数的确切地址不会发生在堆栈上的函数调用，则显示的字节偏移量。  
  
 例如下, 表描述上面的输出的第一行︰  
  
|输出|描述|  
|------------|-----------------|  
|`00427D55:`|最后一个函数调用返回地址。|  
|`DUMP2\DEBUG\DUMP2.EXE!`|包含函数调用的模块的完整路径名称。|  
|`void AfxDumpStack(unsigned long)`|调用的函数原型。|  
|`+ 181 bytes`|以字节为单位发件人的函数原型的地址的偏移量 (在这种情况下， `void AfxDumpStack(unsigned long)`) 到回邮地址 (在这种情况下， `00427D55`)。|  
  
 `AfxDumpStack`可用于调试版本和非调试版本的 MFC 库;但是，即使可执行文件共享 DLL 中使用 MFC 函数会始终以静态方式，链接。 在共享库实现中，在 MFCS42 中找到函数。LIB 库 （和其变化版本）。  
  
 若要成功使用此函数︰  
  
-   该文件了内部错误。DLL 必须位于您的路径。 如果没有此 DLL，该函数将显示一条错误消息。 请参阅[图像帮助库](http://msdn.microsoft.com/library/windows/desktop/ms680321)有关提供了内部错误的函数集合的信息。  
  
-   对堆栈帧的模块必须包括调试信息。 如果它们不包含调试信息，该函数仍将生成堆栈跟踪，但跟踪将有所简化。  
### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameafxenablememoryleakdumpa--afxenablememoryleakdump"></a><a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump  
 启用和禁用 `AFX_DEBUG_STATE` 析构函数中的内存泄漏转储。  
  
```  
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```  
  
### <a name="parameters"></a>参数  
 [in] `bDump`  
 `TRUE` 指示已启用内存泄漏转储；`FALSE` 指示已禁用内存泄漏转储。  
  
### <a name="return-value"></a>返回值  
 此标志的上一个值。  
  
### <a name="remarks"></a>备注  
 当应用程序卸载 MFC 库时，MFC 库将检查内存泄漏。 在这种情况下，通过向用户报告的所有内存泄漏**调试**窗口[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]。  
  
 如果应用程序在加载 MFC 库之前加载另一个库，则会将该库中的一些内存分配误报为内存泄漏。 MFC 库报告错误的内存泄漏时，这些误报可能导致应用程序缓慢关闭。 在这种情况下，使用 `AfxEnableMemoryLeakDump` 禁用内存泄漏转储。  
  
> [!NOTE]
>  如果使用此方法来关闭内存泄漏转储，将不会在应用程序中收到有效内存泄漏的报告。 只有确信内存泄漏报告中包含误报时才使用此方法。  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameafxenablememorytrackinga--afxenablememorytracking"></a><a name="afxenablememorytracking"></a>AfxEnableMemoryTracking  
 在 MFC 的调试版本中正常情况下启用诊断跟踪的内存。  
  
```   
BOOL AfxEnableMemoryTracking(BOOL bTrack); 
```  
  
### <a name="parameters"></a>参数  
 *bTrack*  
 此值设置为**TRUE**开启内存跟踪;**FALSE**会将其关闭。  
  
### <a name="return-value"></a>返回值  
 启用跟踪标志的以前的设置。  
  
### <a name="remarks"></a>备注  
 使用此函数禁用跟踪代码，您知道正在正确分配块的部分。  
  
 有关详细信息`AfxEnableMemoryTracking`，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。  
  
> [!NOTE]
>  此函数仅在 MFC 的调试版本中起作用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&24;](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]  
  
### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameafxismemoryblocka--afxismemoryblock"></a><a name="afxismemoryblock"></a>AfxIsMemoryBlock  
 测试以确保它表示的当前处于活动状态的内存块的诊断版本的已分配的内存地址**新**。  
  
```   
BOOL AfxIsMemoryBlock(
    const void* p,  
    UINT nBytes,  
    LONG* plRequestNumber = NULL); 
```  
  
### <a name="parameters"></a>参数  
 `p`  
 指向内存块的要测试的点。  
  
 `nBytes`  
 包含以字节为单位的内存块的长度。  
  
 `plRequestNumber`  
 指向**长**整数，它将使用的内存块分配序列号，用来填充或如果它不表示当前处于活动状态的内存块为零。  
  
### <a name="return-value"></a>返回值  
 非零，如果当前分配的内存块，并且长度正确。否则为 0。  
  
### <a name="remarks"></a>备注  
 它还检查原始的已分配大小根据指定的大小。 如果该函数将返回非零，以返回分配序列号`plRequestNumber`。 此数字表示相对于所有其他分配该块时的顺序**新**分配。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&27;](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]  
  
### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameafxisvalidaddressa--afxisvalidaddress"></a><a name="afxisvalidaddress"></a>AfxIsValidAddress  
 测试以确保它包含完全在程序的内存空间中任何内存地址。  
  
```   
BOOL AfxIsValidAddress(
    const void* lp,  
    UINT nBytes,  
    BOOL bReadWrite = TRUE); 
```  
  
### <a name="parameters"></a>参数  
 `lp`  
 指向要测试的内存地址。  
  
 `nBytes`  
 包含要进行测试的内存的字节数。  
  
 *bReadWrite*  
 指定的内存是否是同时用于读取和写入 ( **TRUE**) 或只读取 ( **FALSE**)。  
  
### <a name="return-value"></a>返回值  
 在调试版本中，如果指定的内存块，则为非完全中包含该程序的内存空间;否则为 0。  
  
 在非调试生成中，如果非零`lp`不可为 NULL; 否则为 0。  
  
### <a name="remarks"></a>备注  
 该地址并不局限于由分配块**新**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&28;](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]  
  
### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameafxisvalidstringa--afxisvalidstring"></a><a name="afxisvalidstring"></a>AfxIsValidString  
 使用此函数可确定指向字符串的指针是否有效。  
  
```   
BOOL  AfxIsValidString(
    LPCSTR lpsz,  
    int nLength = -1); 
```  
  
### <a name="parameters"></a>参数  
 `lpsz`  
 要测试的指针。  
  
 `nLength`  
 指定要进行测试，以字节为单位的字符串的长度。 值的 â €"1 指示该字符串将以 null 结尾。  
  
### <a name="return-value"></a>返回值  
 在调试版本中，如果指定的指针指向的字符串指定的大小，则非零值否则为 0。  
  
 在非调试生成中，如果非零`lpsz`不可为 NULL; 否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities #&29;](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameafxsetallochooka--afxsetallochook"></a><a name="afxsetallochook"></a>AfxSetAllocHook  
 设置在每个内存块分配之前使指定的函数调用的挂钩。  
  
```   
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook); 
```  
  
### <a name="parameters"></a>参数  
 *pfnAllocHook*  
 指定要调用的函数的名称。 请参阅分配函数的原型的备注部分。  
  
### <a name="return-value"></a>返回值  
 非零，如果您想要允许堆分配。否则为 0。  
  
### <a name="remarks"></a>备注  
 Microsoft 基础类库调试内存分配器可以调用用户定义的挂钩函数，以允许用户来监视内存分配，并控制是否允许分配。 分配挂钩函数是构建出原型，如下所示︰  
  
 **BOOL AFXAPI AllocHook( size_t** `nSize`**, BOOL** `bObject`**, LONG** `lRequestNumber` **);**  
  
 `nSize`  
 建议的内存分配的大小。  
  
 `bObject`  
 **TRUE**如果分配长度为`CObject`-派生的对象; 否则为**FALSE**。  
  
 `lRequestNumber`  
 内存分配序列号。  
  
 请注意， **AFXAPI**调用约定表示被调用方必须删除从堆栈的参数。  

### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameafxdoforallclassesa--afxdoforallclasses"></a><a name="afxdoforallclasses"></a>AfxDoForAllClasses  
 调用指定的迭代函数的所有可序列化`CObject`-应用程序的内存空间中派生类。  
  
```   
void  
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>参数  
 `pfn`  
 指向一个迭代函数以调用每个类。 函数参数是一个指向`CRuntimeClass`对象和函数的调用方提供的额外数据的 void 指针。  
  
 `pContext`  
 指向调用方可以提供对迭代函数的可选数据。 此指针可以为**NULL**。  
  
### <a name="remarks"></a>备注  
 可序列化`CObject`-派生的类是使用派生的类`DECLARE_SERIAL`宏。 将指针传递给`AfxDoForAllClasses`中`pContext`传递给指定的迭代函数每次调用它。  
  
> [!NOTE]
>  此函数仅在 MFC 的调试版本中起作用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&113;](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]  
  
 [!code-cpp[NVC_MFCCollections #&114;](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]  
  
### <a name="requirements"></a>要求  
 **标头：** afx.h 

##  <a name="a-nameafxdoforallobjectsa--afxdoforallobjects"></a><a name="afxdoforallobjects"></a>AfxDoForAllObjects  
 执行指定的迭代函数，为所有对象都派生自`CObject`与已分配的**新**。  
  
```   
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>参数  
 `pfn`  
 指向要为每个对象执行迭代函数。 函数参数是一个指向`CObject`和调用方提供给函数的额外数据的 void 指针。  
  
 `pContext`  
 指向调用方可以提供对迭代函数的可选数据。 此指针可以为**NULL**。  
  
### <a name="remarks"></a>备注  
 不会枚举堆栈，全局或嵌入的对象。 将指针传递给`AfxDoForAllObjects`中`pContext`传递给指定的迭代函数每次调用它。  
  
> [!NOTE]
>  此函数仅在 MFC 的调试版本中起作用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections #&115;](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]  
  
 [!code-cpp[NVC_MFCCollections 排行榜的 #&116;](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
