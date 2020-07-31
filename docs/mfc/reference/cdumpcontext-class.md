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
ms.openlocfilehash: 3a81e06586e6de14d57ce4c4de36dc30c73383f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212509"
---
# <a name="cdumpcontext-class"></a>CDumpContext 类

支持面向流并使用可读文本格式的诊断输出。

## <a name="syntax"></a>语法

```
class CDumpContext
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDumpContext：： CDumpContext](#cdumpcontext)|构造 `CDumpContext` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CDumpContext：:D umpAsHex](#dumpashex)|转储以十六进制格式表示的项。|
|[CDumpContext：： Flush](#flush)|刷新转储上下文缓冲区中的所有数据。|
|[CDumpContext：： GetDepth](#getdepth)|获取对应于转储深度的整数。|
|[CDumpContext：： HexDump](#hexdump)|以十六进制格式转储包含在数组中的字节。|
|[CDumpContext：： SetDepth](#setdepth)|设置转储的深度。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CDumpContext：： operator&lt;&lt;](#operator_lt_lt)|将变量和对象插入转储上下文中。|

## <a name="remarks"></a>备注

`CDumpContext`没有基类。

对于大多数转储，可以使用[afxDump](diagnostic-services.md#afxdump)（预声明 `CDumpContext` 对象）。 `afxDump`对象仅在 Microsoft 基础类库的调试版本中可用。

多个内存[诊断服务](../../mfc/reference/diagnostic-services.md)使用 `afxDump` 它们的输出。

在 Windows 环境下，预定义对象的输出 `afxDump` （在概念上类似于 `cerr` 流）通过 Windows 函数路由到调试器 `OutputDebugString` 。

`CDumpContext` **<<** 对于转储对象数据的指针，类具有重载的插入（）运算符 `CObject` 。 如果需要将自定义转储格式用于派生对象，请重写[CObject：:D ump](../../mfc/reference/cobject-class.md#dump)。 大多数 Microsoft 基础类实现了一个重写的 `Dump` 成员函数。

不是从派生的类 `CObject` ，如 `CString` 、 `CTime` 和 `CTimeSpan` ，它们具有自己的重载 `CDumpContext` 插入运算符，如、和等常用结构 `CFileStatus` `CPoint` `CRect` 。

如果在类的实现中使用[IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic)或[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏，则 `CObject::Dump` 将打印 `CObject` 派生类的名称。 否则，会打印 `CObject` 。

`CDumpContext`类可用于库的调试版本和发布版本，但 `Dump` 成员函数仅在调试版本中定义。 使用 **#ifdef _DEBUG**  /  `#endif` 语句来标记诊断代码，包括自定义 `Dump` 成员函数。

创建自己的对象之前 `CDumpContext` ，必须先创建一个用作 `CFile` 转储目标的对象。

有关的详细信息 `CDumpContext` ，请参阅[调试 MFC 应用程序](/visualstudio/debugger/mfc-debugging-techniques)。

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>继承层次结构

`CDumpContext`

## <a name="requirements"></a>要求

**标头：** afx

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>CDumpContext：： CDumpContext

构造类的对象 `CDumpContext` 。

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>参数

*.Pfile*<br/>
指向作为 `CFile` 转储目标的对象的指针。

### <a name="remarks"></a>备注

`afxDump`自动构造对象。

`CFile`当转储上下文处于活动状态时，请勿写入基础; 否则，将干扰转储。 在 Windows 环境下，通过 Windows 函数将输出路由到调试器 `OutputDebugString` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpContext：:D umpAsHex

转储格式化为十六进制数的指定类型。

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

调用此成员函数以将指定类型的项转储为十六进制数。 若要转储数组，请调用[CDumpContext：： HexDump](#hexdump)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a>CDumpContext：： Flush

强制将缓冲区中剩余的所有数据写入到转储上下文附加的文件。

```cpp
void Flush();
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpContext：： GetDepth

确定深层转储还是浅转储正在处理。

```
int GetDepth() const;
```

### <a name="return-value"></a>返回值

由设置的转储的深度 `SetDepth` 。

### <a name="example"></a>示例

  请参阅[SetDepth](#setdepth)的示例。

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a>CDumpContext：： HexDump

转储格式化为十六进制数的字节数组。

```cpp
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>参数

*lpszLine*<br/>
要在新行的开头输出的字符串。

*pby*<br/>
指向包含要转储的字节的缓冲区的指针。

*nBytes*<br/>
要转储的字节数。

*nWidth*<br/>
每行转储的最大字节数（不是输出行的宽度）。

### <a name="remarks"></a>备注

若要转储单个特定项类型作为十六进制数，请调用[CDumpContext：:D umpashex](#dumpashex)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpContext：： operator&lt;&lt;

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

`CDumpContext` 引用。 使用返回值，可以在源代码的单个行上写入多个插入内容。

### <a name="remarks"></a>备注

对于 `CObject` 指针以及大多数基元类型，插入运算符都是重载的。 指向字符的指针将导致字符串内容的转储;一个指针，它 **`void`** 只会生成地址的十六进制转储。 LONGLONG 会导致转储64位有符号整数;ULONGLONG 会导致转储64位无符号整数。

如果在类的实现中使用 IMPLEMENT_DYNAMIC 或 IMPLEMENT_SERIAL 宏，则插入运算符到 `CObject::Dump` 将打印 `CObject` 派生类的名称。 否则，会打印 `CObject` 。 如果重写 `Dump` 类的函数，则可以提供更有意义的对象内容输出，而不是十六进制转储。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a>CDumpContext：： SetDepth

设置转储的深度。

```cpp
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>参数

*nNewDepth*<br/>
新的深度值。

### <a name="remarks"></a>备注

如果要转储的基元类型或 simple `CObject` 不包含指向其他对象的任何指针，则值0就足够了。 大于0的值指定以递归方式转储所有对象的深度转储。 例如，集合的深层转储将转储集合的所有元素。 您可以在派生类中使用其他特定的深度值。

> [!NOTE]
> 深层转储中未检测到循环引用，并且可能会导致无限循环。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)
