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
ms.openlocfilehash: 4cf3f53d1e238218b4eb892dc92e3c823dcc1296
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630515"
---
# <a name="diagnostic-services"></a>诊断服务

Microsoft 基础类库提供了很多简化调试程序的诊断服务。 这些诊断服务包括宏和全局函数，让你能够跟踪程序的内存分配，在运行时转储对象的内容并打印调试消息。 诊断服务的宏和全局函数可分为以下几类：

- 常规诊断宏

- 常规诊断函数和变量

- 对象诊断函数

这些宏和函数可用于派生自 MFC 调试和发布版本中的 `CObject` 的所有类。 但是, 除了 DEBUG_NEW 和验证在发布版本中不执行任何操作。

在调试库中，所有分配的内存块被一系列的“保护字节”包围。 如果这些字节受到错误内存写入的干扰，诊断例程可以报告问题。 如果包括行：

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

在实现文件中，所有对 **new** 的调用将存储发生内存分配的文件名和行号。 函数 [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) 将显示此附加信息，帮助你确定内存泄漏。 关于诊断输出的其他信息，另请参阅 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 类。

此外，C 运行时库还支持一组可用于调试应用程序的诊断函数。 有关详细信息，请参阅《运行时库参考》中的 [调试例程](../../c-runtime-library/debug-routines.md) 。

### <a name="mfc-general-diagnostic-macros"></a>MFC 常规诊断宏

|||
|-|-|
|[ASSERT](#assert)|如果指定的表达式在库的调试版本中计算为 FALSE, 则打印一条消息, 然后中止程序。|
|[ASSERT_KINDOF](#assert_kindof)|测试对象是指定类的对象还是指定类派生类的对象。|
|[ASSERT_VALID](#assert_valid)|通过调用 `AssertValid` 成员函数测试一个对象的内部有效性；通常从 `CObject`中重写。|
|[DEBUG_NEW](#debug_new)|提供调试模式下用于所有对象分配的文件名和行号以帮助查找内存泄漏。|
|[DEBUG_ONLY](#debug_only)|类似于 ASSERT, 但不会测试表达式的值;适用于只在调试模式下执行的代码。|
|[确保和 ENSURE_VALID](#ensure)|使用验证数据正确性。|
|[THIS_FILE](#this_file)|展开为要编译的文件的名称。|
|[TRACE](#trace)|在库调试版本中提供类似 `printf`的功能。|
|[VERIFY](#verify)|类似于 ASSERT, 但在库的发行版本和调试版本中计算表达式的值。|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC 常规诊断变量和函数

|||
|-|-|
|[afxDump](#afxdump)|将 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 信息发送给调试器输出窗口或调试终端的全局变量。|
|[afxMemDF](#afxmemdf)|控制调试内存分配器行为的全局变量。|
|[AfxCheckError](#afxcheckerror)|用于测试传递的 SCODE 的全局变量, 以查看它是否为错误, 如果是, 则会引发相应的错误。|
|[AfxCheckMemory](#afxcheckmemory)|检查所有当前分配的内存的完整性。|
|[AfxDebugBreak](#afxdebugbreak)|导致执行中断。|
|[AfxDump](#cdumpcontext_in_mfc)|如果在调试器中调用，将在调试时转储对象的状态。|
|[AfxDump](#afxdump)|内部函数, 它在调试时转储对象的状态。|
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
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|取消显示有关对已弃用的 MFC 函数的使用的编译器警告。|

## <a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

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

## <a name="afxdebugbreak"></a> AfxDebugBreak

调用此函数以在执行 MFC 应用程序的调试版本时导致中断`AfxDebugBreak`(在调用的位置)。

### <a name="syntax"></a>语法

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>备注

`AfxDebugBreak`在 MFC 应用程序的发布版本中不起作用, 应删除。 此函数只应在 MFC 应用程序中使用。 使用 Win32 API 版本, `DebugBreak`在非 MFC 应用程序中导致中断。

### <a name="requirements"></a>要求

**标头:** afxver_

##  <a name="assert"></a>  ASSERT

计算其参数。

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>参数

*booleanExpression*<br/>
指定一个计算结果为非零值或0的表达式 (包括指针值)。

### <a name="remarks"></a>备注

如果结果为 0, 则宏打印诊断消息并中止程序。 如果条件为非零, 则不执行任何操作。

诊断消息具有以下形式

`assertion failed in file <name> in line <num>`

其中, *name*是源文件的名称, *num*是在源文件中失败的断言的行号。

在 MFC 的发行版中, 断言不会计算表达式的值, 因此不会中断程序。 如果无论环境如何, 都必须计算表达式, 请使用 VERIFY 宏来替换 ASSERT。

> [!NOTE]
>  此函数仅在 MFC 的调试版本中可用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="assert_kindof"></a>  ASSERT_KINDOF

此宏断言指向的对象是指定类的对象, 或者是从指定类派生的类的对象。

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>参数

classname<br/>
派生类的名称`CObject`。

*pobject*<br/>
指向类对象的指针。

### <a name="remarks"></a>备注

*Pobject*参数应为指向对象的指针, 并且可以是**常量**。 指向的对象和类必须支持`CObject`运行时类信息。 例如, 若要确保`pDocument`是指向`CMyDoc`类的对象或它的任何派生对象的指针, 可以编写代码:

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

`ASSERT_KINDOF`使用宏与编码完全相同:

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

此函数仅适用于使用 [DECLARE_DYNAMIC] (运行时对象模型-DECLARE_DYNAMIC # 或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏声明的类。

> [!NOTE]
>  此函数仅在 MFC 的调试版本中可用。

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="assert_valid"></a>  ASSERT_VALID

用于测试有关对象的内部状态是否有效的假设。

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>参数

*pObject*<br/>
指定派生自`CObject`的类的对象, 该对象具有`AssertValid`成员函数的重写版本。

### <a name="remarks"></a>备注

ASSERT_VALID 调用`AssertValid`作为参数传递的对象的成员函数。

在 MFC 的发行版中, ASSERT_VALID 不执行任何操作。 在调试版本中, 它将验证指针, 检查是否存在 NULL, 并调用该对象自己`AssertValid`的成员函数。 如果这些测试中有任何一个失败, 将以与[声明](#assert)相同的方式显示警报消息。

> [!NOTE]
>  此函数仅在 MFC 的调试版本中可用。

有关详细信息和示例, 请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="debug_new"></a>  DEBUG_NEW

帮助查找内存泄漏。

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>备注

你可以在程序中的任何地方使用 DEBUG_NEW, 这种情况下, 你通常会使用**NEW**运算符来分配堆存储。

在调试模式下 (在定义 **_debug**符号时), DEBUG_NEW 将为它分配的每个对象跟踪文件名和行号。 然后, 当你使用[CMemoryState::D umpallobjectssince](cmemorystate-structure.md#dumpallobjectssince)成员函数时, 将显示使用 DEBUG_NEW 分配的每个对象, 其文件名和行号被分配到该函数。

若要使用 DEBUG_NEW, 请将以下指令插入到源文件中:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

插入此指令后, 预处理器将在任何使用**NEW**的位置插入 DEBUG_NEW, MFC 会执行其余的工作。 编译程序的发行版时, DEBUG_NEW 解析为简单的**新**操作, 并且不生成文件名和行号信息。

> [!NOTE]
>  在以前版本的 MFC (4.1 及更早版本) 中, 需要`#define`将语句放在调用了 IMPLEMENT_DYNCREATE 或 IMPLEMENT_SERIAL 宏的所有语句之后。 这不再是必需的。

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY

在调试模式下 (定义 **_debug**符号时), DEBUG_ONLY 将计算其参数。

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>备注

在发布版本中, DEBUG_ONLY 不会计算其参数。 当你的代码应仅在调试版本中执行时, 这非常有用。

DEBUG_ONLY 宏等效于带有和`#endif`的 `#ifdef _DEBUG`周围表达式。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

### <a name="ensure"></a>确保和 ENSURE_VALID

使用验证数据正确性。

### <a name="syntax"></a>语法

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>参数

*booleanExpression*<br/>
指定要测试的布尔表达式。

### <a name="remarks"></a>备注

这些宏的目的是改进参数的验证。 宏阻止进一步处理代码中错误的参数。 与 ASSERT 宏不同, 确保宏除了生成断言之外还会引发异常。

宏根据项目配置以两种方式表现。 如果断言失败, 宏调用断言并引发异常。 因此, 在调试配置 (即, 在其中定义了 _DEBUG 的位置) 中, 宏在发布配置中生成一个断言和异常, 而宏仅生成异常 (断言不会计算 Release 配置中的表达式)。

宏 ENSURE_ARG 的作用类似于 "确保宏"。

ENSURE_VALID 调用 ASSERT_VALID 宏 (仅在调试版本中起作用)。 此外, 如果指针为 NULL, 则 ENSURE_VALID 将引发异常。 空测试在调试和发布配置中执行。

如果这些测试中有任何一个失败, 将以与声明相同的方式显示警报消息。 如果需要, 宏会引发无效参数异常。
### <a name="requirements"></a>要求

**标头：** afx.h

## <a name="this_file"></a>THIS_FILE

展开为要编译的文件的名称。

### <a name="syntax"></a>语法

```
THIS_FILE
```

### <a name="remarks"></a>备注

此信息由断言和验证宏使用。 应用程序向导和代码向导会将宏放置在创建的源代码文件中。

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

##  <a name="trace"></a>  TRACE

向当前应用程序的调试器发送指定的字符串。

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>备注

有关跟踪的说明, 请参阅[ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) 。 TRACE 和 ATLTRACE2 具有相同的行为。

在 MFC 的调试版本中, 此宏向当前应用程序的调试器发送指定的字符串。 在发布版本中, 此宏编译为 nothing (根本不生成任何代码)。

有关详细信息, 请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="verify"></a>  VERIFY

在 MFC 的调试版本中, 计算其参数。

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>参数

*booleanExpression*<br/>
指定一个计算结果为非零值或0的表达式 (包括指针值)。

### <a name="remarks"></a>备注

如果结果为 0, 则宏打印诊断消息并中止程序。 如果条件为非零, 则不执行任何操作。

诊断消息具有以下形式

`assertion failed in file <name> in line <num>`

其中, *name*是源文件的名称, *num*是在源文件中失败的断言的行号。

在 MFC 的发布版本中, 验证是否计算表达式, 但不打印或中断程序。 例如, 如果表达式是函数调用, 则调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="cdumpcontext_in_mfc"></a>afxDump (MFC 中的 CDumpContext)

在应用程序中提供基本的对象转储功能。

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>备注

`afxDump`是预定义的[CDumpContext](../../mfc/reference/cdumpcontext-class.md)对象, 可用于将`CDumpContext`信息发送到调试器输出窗口或调试终端。 通常, 将作为`afxDump`参数提供给。 `CObject::Dump`

在 windows NT 和所有版本的 windows 下`afxDump` , 调试应用程序时, 会将输出发送到C++ Visual 的 "输出"-"调试" 窗口。

此变量仅在 MFC 的调试版本中定义。 有关的详细信息`afxDump`, 请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

## <a name="afxdump"></a>AfxDump (内部)

MFC 用于在调试时转储对象状态的内部函数。

### <a name="syntax"></a>语法

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>参数

*pOb*<br/>
指向派生自`CObject`的类的对象的指针。

### <a name="remarks"></a>备注

`AfxDump`调用对象的`Dump`成员函数, 并将信息发送到`afxDump`变量指定的位置。 `AfxDump`仅在 MFC 的调试版本中可用。

程序代码不应调用`AfxDump`, 而应`Dump`调用适当对象的成员函数。

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxmemdf"></a>  afxMemDF

可以从调试器或程序访问此变量, 并允许你调整分配诊断。

```
int  afxMemDF;
```

### <a name="remarks"></a>备注

`afxMemDF`可以具有枚举`afxMemDF`指定的下列值:

- `allocMemDF`启用调试分配器 (调试库中的默认设置)。

- `delayFreeMemDF`释放内存的延迟。 当程序释放内存块时, 分配器不会将该内存返回到基础操作系统。 这会对程序施加最大的内存压力。

- `checkAlwaysMemDF`每`AfxCheckMemory`次分配或释放内存时都调用。 这会大大降低内存分配和释放的速度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxcheckerror"></a>  AfxCheckError

此函数测试传递的 SCODE, 以查看是否为错误。

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>备注

如果为错误，则此函数将引发异常。 如果传递的 SCODE 为 E_OUTOFMEMORY, 则该函数将通过调用[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md) 。 否则, 该函数将通过调用[AfxThrowOleException](exception-processing.md#afxthrowoleexception)引发[COleException](../../mfc/reference/coleexception-class.md) 。

此函数可用于检查调用应用程序中的 OLE 函数返回的值。 通过在你的应用程序中使用此函数测试返回值，你可使用最少的代码正确反映错误条件。

> [!NOTE]
>  此函数的效果与调试生成和不调试生成的相同。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxcheckmemory"></a>  AfxCheckMemory

此函数验证可用内存池, 并根据需要打印错误消息。

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>返回值

如果没有内存错误, 则为非零值;否则为0。

### <a name="remarks"></a>备注

如果该函数未检测到任何内存损坏, 则不会进行任何打印。

将检查当前在堆上分配的所有内存块, 包括**新**分配的内存块, 而不是通过直接调用到基础内存分配器分配的内存块, 如`GlobalAlloc` **malloc**函数或 Windows 函数。 如果发现任何块已损坏, 则会向调试器输出输出一条消息。

如果包括行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

在程序模块中, 后续调用以`AfxCheckMemory`显示分配内存的文件名和行号。

> [!NOTE]
>  如果模块包含可序列化类的一个或多个实现, 则必须将`#define`该行置于上一个 IMPLEMENT_SERIAL 宏调用之后。

此函数仅适用于 MFC 的调试版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxdump"></a>AfxDump (MFC)

在调试器中调用此函数, 以便在调试时转储对象的状态。

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>参数

*pOb*<br/>
指向派生自`CObject`的类的对象的指针。

### <a name="remarks"></a>备注

`AfxDump`调用对象的`Dump`成员函数, 并将信息发送到`afxDump`变量指定的位置。 `AfxDump`仅在 MFC 的调试版本中可用。

程序代码不应调用`AfxDump`, 而应`Dump`调用适当对象的成员函数。

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxdumpstack"></a>  AfxDumpStack

此全局函数可用于生成当前堆栈的映像。

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>参数

*dwTarget*<br/>
指示转储输出的目标。 可能的值可以使用按位 "或" ( **&#124;** ) 运算符组合在一起, 如下所示:

- AFX_STACK_DUMP_TARGET_TRACE 通过[跟踪](#trace)宏发送输出。 TRACE 宏仅在调试版本中生成输出;它在发布版本中不会生成任何输出。 此外, TRACE 还可以重定向到调试器之外的其他目标。

- AFX_STACK_DUMP_TARGET_DEFAULT 将转储输出发送到默认目标。 对于调试版本, 输出将转到跟踪宏。 在发布版本中, 输出将转到剪贴板。

- AFX_STACK_DUMP_TARGET_CLIPBOARD 仅将输出发送到剪贴板。 数据将以纯文本形式放置在剪贴板上, 使用 CF_TEXT 剪贴板格式。

- AFX_STACK_DUMP_TARGET_BOTH 同时将输出发送到剪贴板和跟踪宏。

- AFX_STACK_DUMP_TARGET_ODS 通过 Win32 函数`OutputDebugString()`将输出直接发送到调试器。 当调试器附加到进程时, 此选项将在调试和发布版本中生成调试器输出。 AFX_STACK_DUMP_TARGET_ODS 始终到达调试器 (如果已附加), 且无法重定向。

### <a name="remarks"></a>备注

下面的示例反映了从 MFC 对话框应用程序中的按钮`AfxDumpStack`处理程序调用而生成的单行输出:

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

以上输出中的每一行指示最后一个函数调用的地址、包含函数调用的模块的完整路径名称以及名为的函数原型。 如果堆栈上的函数调用不是在函数的确切地址处发生, 则将显示字节偏移量。

例如, 下表描述了上述输出的第一行:

|Output|描述|
|------------|-----------------|
|`00427D55:`|最后一个函数调用的返回地址。|
|`DUMP2\DEBUG\DUMP2.EXE!`|包含函数调用的模块的完整路径名称。|
|`void AfxDumpStack(unsigned long)`|调用的函数原型。|
|`+ 181 bytes`|从函数原型的地址 (在本例中`void AfxDumpStack(unsigned long)`为) 到返回地址 (在`00427D55`本例中为) 的偏移量 (以字节为单位)。|

`AfxDumpStack`MFC 库的调试版本和 nondebug 版本中提供了;但是, 即使可执行文件在共享 DLL 中使用 MFC, 此函数也始终以静态方式链接。 在共享库实现中, 在 MFCS42 中找到该函数。LIB 库 (及其变体)。

若要成功使用此函数:

- IMAGEHLP.DLL 文件。DLL 必须在你的路径上。 如果没有此 DLL, 此函数将显示错误消息。 有关 IMAGEHLP.DLL 提供的函数集的信息, 请参阅[图像帮助库](/windows/win32/Debug/image-help-library)。

- 堆栈上具有框架的模块必须包含调试信息。 如果它们不包含调试信息, 则函数仍将生成堆栈跟踪, 但不会详细说明跟踪。
  ### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxenablememoryleakdump"></a>  AfxEnableMemoryLeakDump

启用和禁用 AFX_DEBUG_STATE 析构函数中的内存泄漏转储。

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>参数

*bDump*<br/>
中如果为 TRUE, 则表示已启用内存泄漏转储;FALSE 表示已禁用内存泄漏转储。

### <a name="return-value"></a>返回值

此标志的上一个值。

### <a name="remarks"></a>备注

当应用程序卸载 MFC 库时，MFC 库将检查内存泄漏。 此时, 任何内存泄露都将通过 Visual Studio 的 "**调试**" 窗口报告给用户。

如果应用程序在加载 MFC 库之前加载另一个库，则会将该库中的一些内存分配误报为内存泄漏。 MFC 库报告错误的内存泄漏时，这些误报可能导致应用程序缓慢关闭。 在这种情况下，使用 `AfxEnableMemoryLeakDump` 禁用内存泄漏转储。

> [!NOTE]
>  如果使用此方法来关闭内存泄漏转储，将不会在应用程序中收到有效内存泄漏的报告。 只有确信内存泄漏报告中包含误报时才使用此方法。

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxenablememorytracking"></a>  AfxEnableMemoryTracking

通常在 MFC 的调试版本中启用诊断内存跟踪。

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>参数

*bTrack*<br/>
如果将此值设置为 TRUE, 则打开内存跟踪;FALSE 将关闭。

### <a name="return-value"></a>返回值

跟踪启用标志的上一个设置。

### <a name="remarks"></a>备注

使用此函数可对你知道已正确分配块的代码部分禁用跟踪。

有关的详细信息`AfxEnableMemoryTracking`, 请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
>  此函数仅适用于 MFC 的调试版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxismemoryblock"></a>  AfxIsMemoryBlock

测试内存地址, 以确保它表示当前活动内存块, 该内存块是由**新**的诊断版本分配的。

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>参数

*p*<br/>
指向要测试的内存块。

*nBytes*<br/>
包含内存块的长度 (以字节为单位)。

*plRequestNumber*<br/>
指向将使用内存块分配序列号填充的**长**整数, 如果它不表示当前活动的内存块, 则为零。

### <a name="return-value"></a>返回值

如果当前已分配内存块且长度正确, 则为非零值;否则为0。

### <a name="remarks"></a>备注

它还会根据原始分配的大小检查指定的大小。 如果该函数返回非零值, 则将在*plRequestNumber*中返回分配序列号。 此数字表示相对于所有其他**新**分配分配块的顺序。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxisvalidaddress"></a>  AfxIsValidAddress

测试任何内存地址, 以确保它完全包含在程序的内存空间中。

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>参数

*lp*<br/>
指向要测试的内存地址。

*nBytes*<br/>
包含要测试的内存字节数。

*bReadWrite*<br/>
指定内存是用于读取和写入 (TRUE), 还是仅用于读取 (FALSE)。

### <a name="return-value"></a>返回值

在调试版本中, 如果指定的内存块完全包含在程序的内存空间中, 则为非零;否则为0。

在非调试版本中, 如果*lp*不为 NULL, 则为非零值;否则为0。

### <a name="remarks"></a>备注

该地址不会限制为**新**分配的块。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxisvalidstring"></a>  AfxIsValidString

使用此函数可确定指向字符串的指针是否有效。

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>参数

*lpsz*<br/>
要测试的指针。

*nLength*<br/>
指定要测试的字符串的长度 (以字节为单位)。 如果值为-1, 则指示字符串将以 null 结尾。

### <a name="return-value"></a>返回值

在调试版本中, 如果指定的指针指向指定大小的字符串, 则为非零值;否则为0。

在非调试版本中, 如果*lpsz*不为 NULL, 则为非零值;否则为0。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxsetallochook"></a>  AfxSetAllocHook

设置在分配每个内存块之前允许调用指定函数的挂钩。

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>参数

*pfnAllocHook*<br/>
指定要调用的函数的名称。 请参阅有关分配函数的原型的备注。

### <a name="return-value"></a>返回值

如果要允许分配, 则为非零值;否则为0。

### <a name="remarks"></a>备注

Microsoft 基础类库调试内存分配器可以调用用户定义的挂钩函数, 以允许用户监视内存分配并控制是否允许分配。 分配挂钩函数的原型如下所示:

**BOOL AFXAPI AllocHook (size_t** `nSize` **, BOOL** `bObject` **, LONG** `lRequestNumber` **);**

*nSize*<br/>
建议的内存分配的大小。

*bObject*<br/>
如果分配用于`CObject`派生对象, 则为 TRUE; 否则为 FALSE。

*lRequestNumber*<br/>
内存分配的序列号。

请注意, AFXAPI 调用约定意味着被调用方必须从堆栈中移除参数。

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxdoforallclasses"></a>  AfxDoForAllClasses

为应用程序的内存空间中的`CObject`所有可序列化派生的类调用指定的迭代函数。

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>参数

*pfn*<br/>
指向要为每个类调用的迭代函数。 函数参数是指向`CRuntimeClass`对象的指针和指向调用方向函数提供的额外数据的 void 指针。

*pContext*<br/>
指向调用方可以提供给迭代函数的可选数据。 此指针可以为 NULL。

### <a name="remarks"></a>备注

可`CObject`序列化的派生类是使用 DECLARE_SERIAL 宏派生的类。 每次调用时, 传递`AfxDoForAllClasses`到*pContext*中的指针都会传递给指定的迭代函数。

> [!NOTE]
>  此函数仅适用于 MFC 的调试版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="afxdoforallobjects"></a>  AfxDoForAllObjects

为派生自`CObject`的所有对象执行指定的迭代函数, 该函数已使用**new**进行分配。

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>参数

*pfn*<br/>
指向要对每个对象执行的迭代函数。 函数参数是指向的`CObject`指针, 指向调用方向函数提供的额外数据的 void 指针。

*pContext*<br/>
指向调用方可以提供给迭代函数的可选数据。 此指针可以为 NULL。

### <a name="remarks"></a>备注

不枚举 Stack、global 或 embedded 对象。 每次调用时`AfxDoForAllObjects` , 传递到*pContext*中的指针都会传递给指定的迭代函数。

> [!NOTE]
>  此函数仅适用于 MFC 的调试版本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>请参阅

[宏和全局](mfc-macros-and-globals.md)<br/>
[CObject::Dump](cobject-class.md#dump)
