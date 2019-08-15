---
title: MFC 使用的回调函数
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 9e51774b2158a81fce05dc0bd27e296e4ad94faa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507703"
---
# <a name="callback-functions-used-by-mfc"></a>MFC 使用的回调函数

Microsoft 基础类库中显示了三个回调函数。 这些回调函数将传递给[cdc:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)、 [Cdc:: GrayString](../../mfc/reference/cdc-class.md#graystring)和[cdc:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)。 请注意, 所有回调函数都必须在返回到 Windows 之前捕获 MFC 异常, 因为异常不能跨回调边界引发。 有关异常的详细信息, 请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

|name||
|----------|-----------------|
|[CDC::EnumObjects 的回调函数](#enum_objects)||
|[CDC::GrayString 的回调函数](#graystring)||
|[Callback Function for CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="enum_objects"></a>CDC:: EnumObjects 的回调函数

*ObjectFunc*名称是应用程序提供的函数名称的占位符。

### <a name="syntax"></a>语法

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>参数

*lpszLogObject*<br/>
指向[LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)或[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)数据结构, 该结构包含有关对象的逻辑特性的信息。

*lpData*<br/>
指向传递给 `EnumObjects` 函数的应用程序提供的数据。

### <a name="return-value"></a>返回值

回调函数返回**int**。此返回值是用户定义的。 如果回调函数返回 0，`EnumObjects` 将提前停止枚举。

### <a name="remarks"></a>备注

必须导出实际名称。

## <a name="graystring"></a>CDC:: GrayString 的回调函数

*OutputFunc*是应用程序提供的回调函数名称的占位符。

### <a name="syntax"></a>语法

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>参数

*hDC*<br/>
向 `nWidth` 标识一个内存设备上下文，该上下文具有宽度和高度至少为 `nHeight` 和 `GrayString` 指定的值的位图。

*lpData*<br/>
指向要绘制的字符串。

*nCount*<br/>
指定要输出的字符数。

### <a name="return-value"></a>返回值

回调函数的返回值必须为 TRUE, 以指示成功;否则为 FALSE。

### <a name="remarks"></a>备注

回调函数 (*OutputFunc*) 必须相对于坐标 (0, 0) 而不是 (*x*, *y*) 绘制图像。

## <a name="setabortproc"></a>CDC:: SetAbortProc 的回调函数

名称*AbortFunc*是应用程序提供的函数名称的占位符。

### <a name="syntax"></a>语法

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>参数

*hPr*<br/>
标识设备上下文。

*代码*<br/>
指定是否发生了错误。 如果未发生错误, 则为0。 如果打印管理器当前磁盘空间不足, 并且如果应用程序等待, 更多的磁盘空间将变为可用, 则 SP_OUTOFDISK。 如果*代码*为 SP_OUTOFDISK, 则应用程序不必中止打印作业。 如果不是, 则必须通过调用`PeekMessage`或`GetMessage` Windows 函数向打印管理器发出。

### <a name="return-value"></a>返回值

如果打印作业要继续, 则中止处理程序函数的返回值为非零值, 如果已取消, 则返回0。

### <a name="remarks"></a>备注

必须按照[CDC:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)的 "备注" 部分所述导出实际名称。

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)
