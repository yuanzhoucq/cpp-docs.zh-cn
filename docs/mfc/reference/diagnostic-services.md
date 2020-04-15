---
title: 诊断服务
ms.date: 11/04/2016
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
ms.openlocfilehash: 8db12a73d64641a52fea3056de8ab3180c9239b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365798"
---
# <a name="diagnostic-services"></a>诊断服务

Microsoft 基础类库提供了很多简化调试程序的诊断服务。 这些诊断服务包括宏和全局函数，让你能够跟踪程序的内存分配，在运行时转储对象的内容并打印调试消息。 诊断服务的宏和全局函数可分为以下几类：

- 常规诊断宏

- 常规诊断函数和变量

- 对象诊断函数

这些宏和函数可用于派生自 MFC 调试和发布版本中的 `CObject` 的所有类。 但是，除DEBUG_NEW和 VERIFY 外，其他所有内容在发布版本中不执行任何操作。

在调试库中，所有分配的内存块被一系列的“保护字节”包围。 如果这些字节受到错误内存写入的干扰，诊断例程可以报告问题。 如果包括行：

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

在实现文件中，所有对 **new** 的调用将存储发生内存分配的文件名和行号。 函数 [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) 将显示此附加信息，帮助你确定内存泄漏。 关于诊断输出的其他信息，另请参阅 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 类。

此外，C 运行时库还支持一组可用于调试应用程序的诊断函数。 有关详细信息，请参阅《运行时库参考》中的 [调试例程](../../c-runtime-library/debug-routines.md) 。

### <a name="mfc-general-diagnostic-macros"></a>MFC 常规诊断宏

|||
|-|-|
|[断言](#assert)|如果库调试版本中的指定表达式的计算结果为 FALSE，则打印一条消息，然后中止程序。|
|[ASSERT_KINDOF](#assert_kindof)|测试对象是指定类的对象还是指定类派生类的对象。|
|[ASSERT_VALID](#assert_valid)|通过调用 `AssertValid` 成员函数测试一个对象的内部有效性；通常从 `CObject`中重写。|
|[DEBUG_NEW](#debug_new)|提供调试模式下用于所有对象分配的文件名和行号以帮助查找内存泄漏。|
|[DEBUG_ONLY](#debug_only)|类似于 ASSERT 但不会测试表达式的值；对仅在调试模式下执行的代码非常有用。|
|[确保和ENSURE_VALID](#ensure)|用于验证数据正确性。|
|[THIS_FILE](#this_file)|展开到正在编译的文件的名称。|
|[跟踪](#trace)|在库调试版本中提供类似 `printf`的功能。|
|[验证](#verify)|类似于 ASSERT，但是可在库发布版本以及调试版本中计算表达式的值。|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC 常规诊断变量和函数

|||
|-|-|
|[afxDump](#afxdump)|将 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 信息发送给调试器输出窗口或调试终端的全局变量。|
|[afxMemDF](#afxmemdf)|控制调试内存分配器行为的全局变量。|
|[AfxCheckError](#afxcheckerror)|用于测试传递的 SCODE 是否出错的全局变量，如果出错，将引发相应的错误。|
|[AfxCheckMemory](#afxcheckmemory)|检查所有当前分配的内存的完整性。|
|[AfxDebugBreak](#afxdebugbreak)|导致执行中断。|
|[AfxDump](#cdumpcontext_in_mfc)|如果在调试器中调用，将在调试时转储对象的状态。|
|[AfxDump](#afxdump)|在调试时转储对象状态的内部函数。|
|[AfxDumpStack](#afxdumpstack)|生成当前堆栈的映像。 此函数始终以静态方式链接。|
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|启用内存泄漏转储。|
|[Afx启用内存跟踪](#afxenablememorytracking)|打开和关闭内存跟踪。|
|[AfxIs内存块](#afxismemoryblock)|验证内存块是否正确分配。|
|[AfxIsValid地址](#afxisvalidaddress)|验证内存地址范围是否在程序边界内。|
|[AfxIsValidString](#afxisvalidstring)|确定一个字符串指针是否有效。|
|[AfxSetAllocHook](#afxsetallochook)|实现每次内存分配的函数调用。|

### <a name="mfc-object-diagnostic-functions"></a>MFC 对象诊断函数

|||
|-|-|
|[阿FXDofor所有类](#afxdoforallclasses)|对支持运行时类型检查的所有 `CObject`派生类执行指定函数。|
|[AfxDofor所有对象](#afxdoforallobjects)|对分配 `CObject`new **的所有**派生对象执行指定函数。|

### <a name="mfc-compilation-macros"></a>MFC 编译宏

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|取消显示有关对已弃用的 MFC 函数的使用的编译器警告。|

## <a name="_afx_secure_no_warnings"></a><a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

取消显示有关对已弃用的 MFC 函数的使用的编译器警告。

### <a name="syntax"></a>语法

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>示例

如果未定义 _AFX_SECURE_NO_WARNINGS，则此代码示例将产生一个编译器警告。

```cpp
// define this before including any afx files in *pch.h* (*stdafx.h* in Visual Studio 2017 and earlier)
#define _AFX_SECURE_NO_WARNINGS
```

```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a><a name="afxdebugbreak"></a>AfxDebugBreak

调用此函数以在执行 MFC 应用程序的调试版本时导致中断`AfxDebugBreak`（在调用到的位置）。

### <a name="syntax"></a>语法

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>备注

`AfxDebugBreak`在 MFC 应用程序的发布版本中不起作用，应删除。 此功能应仅在 MFC 应用程序中使用。 使用 Win32 API`DebugBreak`版本 ，会导致非 MFC 应用程序中的中断。

### <a name="requirements"></a>要求

**标题：** afxver_.h

## <a name="assert"></a><a name="assert"></a>断言

评估其参数。

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>参数

*布尔表达式*<br/>
指定计算为非零或 0 的表达式（包括指针值）。

### <a name="remarks"></a>备注

如果结果为 0，宏将打印诊断消息并中止程序。 如果条件为非零，则不执行任何操作。

诊断消息具有以下形式

`assertion failed in file <name> in line <num>`

*其中名称*是源文件的名称 *，num*是源文件中失败的断言的行号。

在 MFC 的发布版本中，ASSERT 不计算表达式，因此不会中断程序。 如果无论环境如何，都必须计算表达式，请使用 VERIFY 宏代替 ASSERT。

> [!NOTE]
> 此功能仅在 MFC 的调试版本中可用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="assert_kindof"></a><a name="assert_kindof"></a>ASSERT_KINDOF

此宏断言指向的对象是指定类的对象，或者是从指定类派生的类的对象。

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>参数

*类名*<br/>
`CObject`派生类的名称。

*pobject*<br/>
指向类对象的指针。

### <a name="remarks"></a>备注

*pobject*参数应是指向对象的指针，并且可以是**const**。 对象指向，类必须支持`CObject`运行时类信息。 例如，为了确保它是`pDocument`指向`CMyDoc`类或其任何衍生物的对象的指针，您可以编写代码：

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

使用`ASSERT_KINDOF`宏与编码完全相同：

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

此函数仅适用于使用 [DECLARE_DYNAMIC]（运行时-对象-服务.md_declare_dynamic 或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏声明的类。

> [!NOTE]
> 此功能仅在 MFC 的调试版本中可用。

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="assert_valid"></a><a name="assert_valid"></a>ASSERT_VALID

用于测试有关对象内部状态有效性的假设。

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>参数

*pObject*<br/>
指定派生自`CObject`具有`AssertValid`成员函数重写版本的类的对象。

### <a name="remarks"></a>备注

ASSERT_VALID调用作为`AssertValid`参数传递的对象的成员函数。

在 MFC 的发布版本中，ASSERT_VALID不执行任何操作。 在调试版本中，它验证指针，检查 NULL，并调用对象自己的`AssertValid`成员函数。 如果其中任何一个测试失败，警报消息的显示方式与[ASSERT](#assert)相同。

> [!NOTE]
> 此功能仅在 MFC 的调试版本中可用。

有关详细信息和示例，请参阅调试[MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="debug_new"></a><a name="debug_new"></a>DEBUG_NEW

协助查找内存泄漏。

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>备注

您可以在程序中的任何地方使用DEBUG_NEW，通常使用**新**运算符分配堆存储。

在调试模式下（定义 **_DEBUG**符号时），DEBUG_NEW跟踪它分配的每个对象的文件名和行号。 然后，当您使用[CMemoryState：:DumpAllObjects 由于](cmemorystate-structure.md#dumpallobjectssince)成员函数，使用DEBUG_NEW分配的每个对象都显示文件名和行号。

若要使用DEBUG_NEW，请将以下指令插入到源文件中：

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

插入此指令后，预处理器将在使用**新**时插入DEBUG_NEW，MFC 将执行其余操作。 编译程序的发布版本时，DEBUG_NEW解析为简单的**新**操作，并且不会生成文件名和行号信息。

> [!NOTE]
> 在早期版本的 MFC（4.1 和更早版本）中，您需要将`#define`语句放在调用IMPLEMENT_DYNCREATE或IMPLEMENT_SERIAL宏的所有语句之后。 现在已没有必要。

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="debug_only"></a><a name="debug_only"></a>DEBUG_ONLY

在调试模式下（定义 **_DEBUG**符号时），DEBUG_ONLY计算其参数。

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>备注

在发布版本中，DEBUG_ONLY不评估其参数。 当您的代码应仅在调试生成中执行时，这非常有用。

DEBUG_ONLY宏等效于 带`#ifdef _DEBUG`的`#endif`周围*表达式*。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

### <a name="ensure-and-ensure_valid"></a><a name="ensure"></a>确保和ENSURE_VALID

用于验证数据正确性。

### <a name="syntax"></a>语法

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>参数

*布尔表达式*<br/>
指定要测试的布尔表达式。

### <a name="remarks"></a>备注

这些宏的目的是改进参数的验证。 宏可防止进一步处理代码中不正确的参数。 与 ASSERT 宏不同，"确保"宏除了生成断言外，还引发异常。

宏根据项目配置以两种方式工作。 宏调用 ASSERT，然后在断言失败时引发异常。 因此，在调试配置（即定义_DEBUG）中，宏生成断言和异常，而在发布配置中，宏仅生成异常（ASSERT 不评估发布配置中的表达式）。

宏ENSURE_ARG类似于"确保"宏。

ENSURE_VALID调用ASSERT_VALID宏（仅在调试生成中具有效果）。 此外，如果指针为 NULL，ENSURE_VALID将引发异常。 NULL 测试在调试和发布配置中都执行。

如果其中任何一个测试失败，警报消息的显示方式与 ASSERT 相同。 如果需要，宏将引发无效的参数异常。

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="this_file"></a><a name="this_file"></a>THIS_FILE

展开到正在编译的文件的名称。

### <a name="syntax"></a>语法

```
THIS_FILE
```

### <a name="remarks"></a>备注

该信息由 ASSERT 和 VERIFY 宏使用。 应用程序向导和代码向导将宏放在他们创建的源代码文件中。

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

**标题：** afx.h

## <a name="trace"></a><a name="trace"></a>跟踪

将指定的字符串发送到当前应用程序的调试器。

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>备注

有关 TRACE 的说明，请参阅[ATLTRACE2。](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) TRACE 和 ATLTRACE2 具有相同的行为。

在 MFC 的调试版本中，此宏将指定的字符串发送到当前应用程序的调试器。 在发布版本中，此宏不会编译到任何内容（根本不生成任何代码）。

有关详细信息，请参阅调试[MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="verify"></a><a name="verify"></a>验证

在 MFC 的调试版本中，评估其参数。

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>参数

*布尔表达式*<br/>
指定计算为非零或 0 的表达式（包括指针值）。

### <a name="remarks"></a>备注

如果结果为 0，宏将打印诊断消息并停止程序。 如果条件为非零，则不执行任何操作。

诊断消息具有以下形式

`assertion failed in file <name> in line <num>`

*其中名称*是源文件的名称 *，num*是源文件中失败的断言的行号。

在 MFC 的发布版本中，VERIFY 会评估表达式，但不会打印或中断程序。 例如，如果表达式是函数调用，则将发出调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxdump-cdumpcontext-in-mfc"></a><a name="cdumpcontext_in_mfc"></a>afxDump（MFC 中的 CDumpContext）

在应用程序中提供基本的对象转储功能。

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>备注

`afxDump`是预定义的[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象，允许您将信息`CDumpContext`发送到调试器输出窗口或调试终端。 通常，作为参数`afxDump`提供 到`CObject::Dump`。

在 Windows NT 和所有版本的`afxDump`Windows 下，在调试应用程序时，输出将发送到可视化C++的输出调试窗口。

此变量仅在 MFC 的调试版本中定义。 有关详细信息，`afxDump`请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxdump-internal"></a><a name="afxdump"></a>AfxDump（内部）

MFC 用于在调试时转储对象状态的内部函数。

### <a name="syntax"></a>语法

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>参数

*Pob*<br/>
指向派生自`CObject`的类对象的指针。

### <a name="remarks"></a>备注

`AfxDump`调用对象`Dump`的成员函数并将信息发送到`afxDump`变量指定的位置。 `AfxDump`仅在 MFC 的调试版本中可用。

程序代码不应调用`AfxDump`，而应调用相应对象`Dump`的成员函数。

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxmemdf"></a><a name="afxmemdf"></a>afxMemDF

此变量可从调试器或程序访问，并允许您调整分配诊断。

```
int  afxMemDF;
```

### <a name="remarks"></a>备注

`afxMemDF`可以具有枚举指定的以下值`afxMemDF`：

- `allocMemDF`打开调试分配器（调试库中的默认设置）。

- `delayFreeMemDF`延迟释放内存。 当程序释放内存块时，分配器不会将该内存返回到基础操作系统。 这将对程序造成最大的内存压力。

- `checkAlwaysMemDF``AfxCheckMemory`每次分配或释放内存时调用。 这将显著减缓内存分配和处理。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxcheckerror"></a><a name="afxcheckerror"></a>AfxCheck错误

此函数将测试传递的 SCODE 以查看它是否是错误。

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>备注

如果为错误，则此函数将引发异常。 如果传递的 SCODE E_OUTOFMEMORY，则函数通过调用[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)引发[CMemoryException。](../../mfc/reference/cmemoryexception-class.md) 否则，函数通过调用[AfxThrowOleException](exception-processing.md#afxthrowoleexception)引发[COleException。](../../mfc/reference/coleexception-class.md)

此函数可用于检查调用应用程序中的 OLE 函数返回的值。 通过在你的应用程序中使用此函数测试返回值，你可使用最少的代码正确反映错误条件。

> [!NOTE]
> 此函数的效果与调试生成和不调试生成的相同。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxcheckmemory"></a><a name="afxcheckmemory"></a>AfxCheck内存

此函数验证可用内存池并根据需要打印错误消息。

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>返回值

如果没有内存错误，则非零;否则 0。

### <a name="remarks"></a>备注

如果函数未检测到内存损坏，则不会打印任何内容。

将检查当前在堆上分配的所有内存块，包括**由新**分配但未通过直接调用基础内存分配器（如**malloc**函数或`GlobalAlloc`Windows 函数）分配的内存块。 如果发现任何块已损坏，则会将消息打印到调试器输出。

如果包含行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

在程序模块中，然后后续调用以`AfxCheckMemory`显示分配内存的文件名和行号。

> [!NOTE]
> 如果模块包含可序列化类的一个或多个实现，则必须将`#define`该行放在最后一个IMPLEMENT_SERIAL宏调用之后。

此函数仅适用于 MFC 的调试版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxdump-mfc"></a><a name="afxdump"></a>AfxDump （MFC）

在调试器中调用此函数，以在调试时转储对象的状态。

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>参数

*Pob*<br/>
指向派生自`CObject`的类对象的指针。

### <a name="remarks"></a>备注

`AfxDump`调用对象`Dump`的成员函数并将信息发送到`afxDump`变量指定的位置。 `AfxDump`仅在 MFC 的调试版本中可用。

程序代码不应调用`AfxDump`，而应调用相应对象`Dump`的成员函数。

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxdumpstack"></a><a name="afxdumpstack"></a>AfxDumpStack

此全局函数可用于生成当前堆栈的映像。

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>参数

*dwTarget*<br/>
指示转储输出的目标。 可以使用位 OR （ **&#124;**） 运算符组合的可能值如下所示：

- AFX_STACK_DUMP_TARGET_TRACE通过[TRACE](#trace)宏发送输出。 TRACE 宏仅在调试生成中生成输出;它在发布版本中不生成输出。 此外，TRACE 可以重定向到调试器之外的其他目标。

- AFX_STACK_DUMP_TARGET_DEFAULT将转储输出发送到默认目标。 对于调试生成，输出将转到 TRACE 宏。 在版本版本中，输出将转到剪贴板。

- AFX_STACK_DUMP_TARGET_CLIPBOARD仅将输出发送到剪贴板。 使用CF_TEXT剪贴板格式，数据以纯文本形式放置在剪贴板上。

- AFX_STACK_DUMP_TARGET_BOTH同时将输出发送到剪贴板和 TRACE 宏。

- AFX_STACK_DUMP_TARGET_ODS通过 Win32 函数`OutputDebugString()`将输出直接发送到调试器。 当调试器附加到进程时，此选项将在调试和发布版本中生成调试器输出。 AFX_STACK_DUMP_TARGET_ODS始终到达调试器（如果已连接），并且无法重定向。

### <a name="remarks"></a>备注

下面的示例反映了从 MFC 对话框应用程序中的按钮处理程序`AfxDumpStack`调用生成的输出的一行：

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

上面输出中的每一行指示最后一个函数调用的地址、包含函数调用的模块的完整路径名称以及调用的函数原型。 如果堆栈上的函数调用未在函数的确切地址发生，则显示字节的偏移量。

例如，下表描述了上述输出的第一行：

|输出|说明|
|------------|-----------------|
|`00427D55:`|最后一个函数调用的返回地址。|
|`DUMP2\DEBUG\DUMP2.EXE!`|包含函数调用的模块的完整路径名称。|
|`void AfxDumpStack(unsigned long)`|调用的功能原型。|
|`+ 181 bytes`|从函数原型的地址（在本例中）`void AfxDumpStack(unsigned long)`到返回地址（在本例中为） 的偏移（在本例中为`00427D55`）。|

`AfxDumpStack`在 MFC 库的调试和非调试版本中可用;但是，即使可执行文件在共享 DLL 中使用 MFC，该函数始终以静态方式链接。 在共享库实现中，该函数位于 MFCS42 中。LIB 库（及其变体）。

要成功使用此功能，请使用：

- 文件图像HLP。DLL 必须位于您的路径上。 如果没有此 DLL，该函数将显示一条错误消息。 有关 IMAGEHLP 提供的函数集的信息，请参阅[图像帮助库](/windows/win32/Debug/image-help-library)。

- 堆栈上具有帧的模块必须包括调试信息。 如果它们不包含调试信息，则函数仍将生成堆栈跟踪，但跟踪将不太详细。

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxenablememoryleakdump"></a><a name="afxenablememoryleakdump"></a>Afxenable内存泄漏转储

启用并禁用AFX_DEBUG_STATE析构函数中的内存泄漏转储。

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>参数

*b转储*<br/>
[在]TRUE 表示内存泄漏转储已启用;如果已启用，则为 TRUE。FALSE 表示内存泄漏转储已禁用。

### <a name="return-value"></a>返回值

此标志的上一个值。

### <a name="remarks"></a>备注

当应用程序卸载 MFC 库时，MFC 库将检查内存泄漏。 此时，任何内存泄漏都通过 Visual Studio 的**调试**窗口报告给用户。

如果应用程序在加载 MFC 库之前加载另一个库，则会将该库中的一些内存分配误报为内存泄漏。 MFC 库报告错误的内存泄漏时，这些误报可能导致应用程序缓慢关闭。 在这种情况下，使用 `AfxEnableMemoryLeakDump` 禁用内存泄漏转储。

> [!NOTE]
> 如果使用此方法来关闭内存泄漏转储，将不会在应用程序中收到有效内存泄漏的报告。 只有确信内存泄漏报告中包含误报时才使用此方法。

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxenablememorytracking"></a><a name="afxenablememorytracking"></a>Afx启用内存跟踪

诊断内存跟踪通常在 MFC 的调试版本中启用。

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>参数

*b轨道*<br/>
将此值设置为 TRUE 将打开内存跟踪;FALSE 将其关闭。

### <a name="return-value"></a>返回值

跟踪启用标志的上一个设置。

### <a name="remarks"></a>备注

使用此函数可以禁用对代码部分的跟踪，您知道这些部分正在正确分配块。

有关详细信息，`AfxEnableMemoryTracking`请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
> 此函数仅适用于 MFC 的调试版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxismemoryblock"></a><a name="afxismemoryblock"></a>AfxIs内存块

测试内存地址，以确保它表示由**new**的诊断版本分配的当前活动内存块。

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>参数

*P*<br/>
指向要测试的内存块。

*n 字节*<br/>
包含以字节为单位的内存块的长度。

*plRequest编号*<br/>
指向将用**long**内存块的分配序列号填充的长整数，如果它不表示当前活动内存块，则指向零。

### <a name="return-value"></a>返回值

如果当前分配了内存块且长度正确，则非零;否则 0。

### <a name="remarks"></a>备注

它还根据原始分配的大小检查指定的大小。 如果函数返回非零，则分配序列号将在*plRequestNumber*中返回。 此数字表示块相对于所有其他**新**分配的分配顺序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxisvalidaddress"></a><a name="afxisvalidaddress"></a>AfxIsValid地址

测试任何内存地址，以确保它完全包含在程序的内存空间中。

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>参数

*lp*<br/>
指向要测试的内存地址。

*n 字节*<br/>
包含要测试的内存字节数。

*bReadWrite*<br/>
指定内存是用于读取和写入 （TRUE） 还是仅用于读取 （FALSE）。

### <a name="return-value"></a>返回值

在调试生成中，如果指定的内存块完全包含在程序的内存空间中，则非零;否则 0。

在非调试生成中，如果*lp*不是 NULL，则非零;否则 0。

### <a name="remarks"></a>备注

该地址不限于**由 new**分配的块。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxisvalidstring"></a><a name="afxisvalidstring"></a>AfxIs 有效字符串

使用此函数可确定指向字符串的指针是否有效。

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>参数

*lpsz*<br/>
要测试的指针。

*n 长度*<br/>
指定要测试的字符串的长度（以字节为单位）。 值 -1 表示字符串将为 null 终止。

### <a name="return-value"></a>返回值

在调试生成中，如果指定的指针指向指定大小的字符串，则非零;否则 0。

在非调试生成中，如果*lpsz*不是 NULL，则非零;否则 0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxsetallochook"></a><a name="afxsetallochook"></a>阿FXSetAllocHook

设置一个挂钩，在分配每个内存块之前启用指定函数的调用。

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>参数

*普芬·洛克胡克*<br/>
指定要调用的函数的名称。 有关分配函数的原型，请参阅备注。

### <a name="return-value"></a>返回值

如果要允许分配，则非零;否则 0。

### <a name="remarks"></a>备注

Microsoft 基础类库调试内存分配器可以调用用户定义的挂钩函数，以允许用户监视内存分配并控制是否允许分配。 分配挂钩函数的原型化如下：

**BOOL AFXAPI 阿洛克胡克（size_t，** `nSize` **BOOL** `bObject` **， 长**`lRequestNumber` **）;**

*nSize*<br/>
建议内存分配的大小。

*bObject*<br/>
如果分配是派生`CObject`对象的，则为 TRUE;否则 FALSE。

*l请求号码*<br/>
内存分配的序列号。

请注意，AFXAPI 调用约定意味着被调用人必须从堆栈中删除参数。

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxdoforallclasses"></a><a name="afxdoforallclasses"></a>阿FXDofor所有类

调用应用程序内存空间中所有可`CObject`序列化派生类的指定迭代函数。

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>参数

*普芬*<br/>
指向要为每个类调用的迭代函数。 函数参数是指向`CRuntimeClass`对象的指针和指向调用方提供到函数的额外数据的空指针。

*pContext*<br/>
指向调用方可以向迭代函数提供的可选数据。 此指针可以是 NULL。

### <a name="remarks"></a>备注

可`CObject`序列化派生类是使用DECLARE_SERIAL宏派生的类。 每次调用*pContext* `AfxDoForAllClasses`中传递给的指针都会传递给指定的迭代函数。

> [!NOTE]
> 此函数仅适用于 MFC 的调试版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>要求

**标题：** afx.h

## <a name="afxdoforallobjects"></a><a name="afxdoforallobjects"></a>AfxDofor所有对象

为派生自`CObject`已使用**new**分配的所有对象执行指定的迭代函数。

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>参数

*普芬*<br/>
指向要为每个对象执行的迭代函数。 函数参数是指向 a`CObject`的指针，是指向调用方向函数提供的额外数据的空指针。

*pContext*<br/>
指向调用方可以向迭代函数提供的可选数据。 此指针可以是 NULL。

### <a name="remarks"></a>备注

不会枚举堆栈、全局或嵌入对象。 每次调用`AfxDoForAllObjects`*pContext*中传递到的指针都会传递给指定的迭代函数。

> [!NOTE]
> 此函数仅适用于 MFC 的调试版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](mfc-macros-and-globals.md)<br/>
[CObject：:Dump](cobject-class.md#dump)
