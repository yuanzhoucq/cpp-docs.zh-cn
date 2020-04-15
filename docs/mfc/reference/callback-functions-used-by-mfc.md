---
title: MFC 使用的回调函数
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 8d84f939795e768c6b1356dcd8dc291421aedfdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371137"
---
# <a name="callback-functions-used-by-mfc"></a>MFC 使用的回调函数

微软基础类库中有三个回调函数。 这些回调函数传递给[CDC：：枚举对象](../../mfc/reference/cdc-class.md#enumobjects)[、CDC：：灰色字符串](../../mfc/reference/cdc-class.md#graystring)和[CDC：：SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)。 请注意，所有回调函数在返回到 Windows 之前都必须捕获 MFC 异常，因为异常不能跨回调边界引发。 有关异常的详细信息，请参阅文章["例外](../../mfc/exception-handling-in-mfc.md)"。

|名称||
|----------|-----------------|
|[CDC::EnumObjects 的回调函数](#enum_objects)||
|[CDC::GrayString 的回调函数](#graystring)||
|[Callback Function for CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="callback-function-for-cdcenumobjects"></a><a name="enum_objects"></a>CDC 的回调函数：：枚举对象

*ObjectFunc*名称是应用程序提供的函数名称的占位符。

### <a name="syntax"></a>语法

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>参数

*lpszLogObject*<br/>
指向包含有关对象逻辑属性的信息的[LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)或[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)数据结构。

*lpData*<br/>
指向传递给 `EnumObjects` 函数的应用程序提供的数据。

### <a name="return-value"></a>返回值

回调函数返回**int**。此返回的值由用户定义。 如果回调函数返回 0，`EnumObjects` 将提前停止枚举。

### <a name="remarks"></a>备注

必须导出实际名称。

## <a name="callback-function-for-cdcgraystring"></a><a name="graystring"></a>CDC 的回调函数：：灰色字符串

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

回调函数的返回值必须是 TRUE 才能指示成功；否则它是 FALSE。

### <a name="remarks"></a>备注

回调函数 *（OutputFunc*） 必须绘制相对于坐标 （0，0） 而不是 *（x*， *y*） 的图像。

## <a name="callback-function-for-cdcsetabortproc"></a><a name="setabortproc"></a>CDC 的回调功能：：SetAbortProc

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
指定是否发生了错误。 如果未发生错误，则为 0。 如果打印管理器当前磁盘空间不足，并且如果应用程序等待，则更多的磁盘空间将变为可用，SP_OUTOFDISK。 如果*代码*SP_OUTOFDISK，则应用程序不必中止打印作业。 否则，它必须通过调用`PeekMessage`或`GetMessage`Windows 函数屈服于打印管理器。

### <a name="return-value"></a>返回值

如果打印作业要继续，中止处理程序函数的返回值为非零;如果取消，则返回值为 0。

### <a name="remarks"></a>备注

实际名称必须导出，如 CDC 的备注部分[所述：setAbortProc](../../mfc/reference/cdc-class.md#setabortproc)。

## <a name="see-also"></a>另请参阅

[结构、样式、回调和消息映射](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC：：枚举对象](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC：：SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC：：灰色字符串](../../mfc/reference/cdc-class.md#graystring)
