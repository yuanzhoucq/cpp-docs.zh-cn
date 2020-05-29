---
title: CDumpContext 类
ms.date: 11/04/2016
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
ms.openlocfilehash: e89bbc5f263dc9303140e43914619090109b8315
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753210"
---
# <a name="cdumpcontext-class"></a>CDumpContext 类

支持面向流并使用可读文本格式的诊断输出。

## <a name="syntax"></a>语法

```
class CDumpContext
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 转储上下文：：C 转储上下文](#cdumpcontext)|构造 `CDumpContext` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDumpContext：:D](#dumpashex)|以十六进制格式转储指示的项。|
|[CDumpContext：冲洗](#flush)|刷新转储上下文缓冲区中的任何数据。|
|[CDumpContext：获取深度](#getdepth)|获取与转储深度对应的整数。|
|[CDump 上下文：十六进制转储](#hexdump)|以十六进制格式转储数组中包含的字节。|
|[CDump 上下文：：设置深度](#setdepth)|设置转储的深度。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CDumpContext：：运算符&lt;&lt;](#operator_lt_lt)|将变量和对象插入转储上下文。|

## <a name="remarks"></a>备注

`CDumpContext`没有基类。

对于大多数转储，您可以使用[afxDump，](diagnostic-services.md#afxdump)一个预申报`CDumpContext`的对象。 该`afxDump`对象仅在 Microsoft 基础类库的调试版本中可用。

多个内存[诊断服务](../../mfc/reference/diagnostic-services.md)用于`afxDump`输出。

在 Windows 环境下，预定义`afxDump`对象的输出在概念上与`cerr`流类似，通过 Windows 函数`OutputDebugString`路由到调试器。

类`CDumpContext`具有转储对象数据的**<<**`CObject`指针的重载插入 （ ） 运算符。 如果需要派生对象的自定义转储格式，则重写[CObject：:Dump](../../mfc/reference/cobject-class.md#dump)。 大多数 Microsoft 基础类实现重写`Dump`的成员函数。

不派生于`CObject`的类（如`CString`、`CTime`和`CTimeSpan`）具有自己的重载插入`CDumpContext`运算符，通常使用的结构（如`CFileStatus`、`CPoint`和`CRect`）也具有重载。

如果在类的实现中使用[IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic)或[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏，则`CObject::Dump`将打印`CObject`派生类的名称。 否则，它将打印`CObject`。

类`CDumpContext`同时可用于库的调试版本和发布版本，但`Dump`成员函数仅在调试版本中定义。 使用 **#ifdef_DEBUG** / `#endif`语句来对诊断代码（包括自定义`Dump`成员函数）进行括号。

在创建自己的`CDumpContext`对象之前，必须创建用作转储目标`CFile`的对象。

有关详细信息，`CDumpContext`请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

**#define_DEBUG**

## <a name="inheritance-hierarchy"></a>继承层次结构

`CDumpContext`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>C 转储上下文：：C 转储上下文

构造类`CDumpContext`的对象 。

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>参数

*pFile*<br/>
指向作为转储目标`CFile`的对象的指针。

### <a name="remarks"></a>备注

对象`afxDump`将自动构造。

转储上下文处于活动状态时，不要`CFile`写入基础;否则，您将干扰转储。 在 Windows 环境中，输出通过 Windows 函数`OutputDebugString`路由到调试器。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpContext：:D

转储格式化为十六进制数字的指定类型。

```
CDumpContext& DumpAsHex(BYTE b);
CDumpContext& DumpAsHex(DWORD dw);
CDumpContext& DumpAsHex(int n);
CDumpContext& DumpAsHex(LONG l);
CDumpContext& DumpAsHex(LONGLONG n);
CDumpContext& DumpAsHex(UINT u);
CDumpContext& DumpAsHex(ULONGLONG n);
CDumpContext& DumpAsHex(WORD w);
```

### <a name="return-value"></a>返回值

对 `CDumpContext` 对象的引用。

### <a name="remarks"></a>备注

调用此成员函数将指定类型的项转储为十六进制数字。 要转储数组，请调用[CDumpContext：：十六进制转储](#hexdump)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a>CDumpContext：冲洗

强制将缓冲区中剩余的任何数据写入附加到转储上下文的文件。

```cpp
void Flush();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpContext：获取深度

确定深度转储还是浅转储正在进行中。

```
int GetDepth() const;
```

### <a name="return-value"></a>返回值

由 设置的转储的深度`SetDepth`。

### <a name="example"></a>示例

  请参阅[SetDepth](#setdepth)的示例。

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a>CDump 上下文：十六进制转储

转储格式化为十六进制数字的字节数组。

```cpp
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>参数

*lpszLine*<br/>
要在新行开始时输出的字符串。

*皮比*<br/>
指向包含要转储的字节的缓冲区的指针。

*n 字节*<br/>
要转储的字节数。

*n 宽度*<br/>
每行转储的最大字节数（不是输出线的宽度）。

### <a name="remarks"></a>备注

要将单个特定项类型转储为十六进制编号，请调用[CDumpContext：:DumpAsHex](#dumpashex)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpContext：：运算符&lt;&lt;

将指定的数据输出到转储上下文。

```
CDumpContext& operator<<(const CObject* pOb);
CDumpContext& operator<<(const CObject& ob);
CDumpContext& operator<<(LPCTSTR lpsz);
CDumpContext& operator<<(const void* lp);
CDumpContext& operator<<(BYTE by);
CDumpContext& operator<<(WORD w);
CDumpContext& operator<<(DWORD dw);
CDumpContext& operator<<(int n);
CDumpContext& operator<<(double d);
CDumpContext& operator<<(float f);
CDumpContext& operator<<(LONG l);
CDumpContext& operator<<(UINT u);
CDumpContext& operator<<(LPCWSTR lpsz);
CDumpContext& operator<<(LPCSTR lpsz);
CDumpContext& operator<<(LONGLONG n);
CDumpContext& operator<<(ULONGLONG n);
CDumpContext& operator<<(HWND h);
CDumpContext& operator<<(HDC h);
CDumpContext& operator<<(HMENU h);
CDumpContext& operator<<(HACCEL h);
CDumpContext& operator<<(HFONT h);
```

### <a name="return-value"></a>返回值

`CDumpContext` 引用。 使用返回值，可以在一行源代码上写入多个插入。

### <a name="remarks"></a>备注

对于`CObject`指针以及大多数基元类型，插入运算符过载。 指向字符的指针会导致字符串内容转储;指向**void 的**指针仅会导致地址的十六进制转储。 LONGLONG 会导致 64 位签名整数的转储;ULONGLONG 会导致 64 位无符号整数的转储。

如果在类的实现中使用IMPLEMENT_DYNAMIC或IMPLEMENT_SERIAL宏，则插入运算符 通过`CObject::Dump`将打印`CObject`派生类的名称。 否则，它将打印`CObject`。 如果重写类`Dump`的函数，则可以提供对象内容的更有意义的输出，而不是十六进制转储。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a>CDump 上下文：：设置深度

设置转储的深度。

```cpp
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>参数

*n 纽里*<br/>
新的深度值。

### <a name="remarks"></a>备注

如果要转储不包含指向其他对象的指针的基`CObject`元类型或简单，则值 0 就足够了。 大于 0 的值指定一个深转储，其中所有对象都递归地转储。 例如，集合的深层转储将转储集合的所有元素。 您可以在派生类中使用其他特定深度值。

> [!NOTE]
> 在深转储中未检测到循环引用，并可能导致无限循环。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)
