---
title: MFC 使用的回调函数
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.functions
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: e3440530dfe30b6667012c76b2904dbb2786c199
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262293"
---
# <a name="callback-functions-used-by-mfc"></a>MFC 使用的回调函数

在 Microsoft 基础类库中显示三个回调函数。 这些回调函数传递给[cdc:: enumobjects](../../mfc/reference/cdc-class.md#enumobjects)， [cdc:: graystring](../../mfc/reference/cdc-class.md#graystring)，并[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)。 请注意所有回调函数必须返回到 Windows，因为不能跨回调边界引发异常之前都捕获 MFC 异常。 有关异常的详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。

|name||
|----------|-----------------|
|[CDC::EnumObjects 的回调函数](#enum_objects)||
|[CDC::GrayString 的回调函数](#graystring)||
|[Callback Function for CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="enum_objects"></a> Cdc:: enumobjects 的回调函数

*ObjectFunc*名称是应用程序提供的函数名称的占位符。

### <a name="syntax"></a>语法

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>参数

*lpszLogObject*<br/>
指向[LOGPEN](/windows/desktop/api/Wingdi/ns-wingdi-taglogpen)或[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)数据结构，其中包含的对象的逻辑特性信息。

*lpData*<br/>
指向传递给 `EnumObjects` 函数的应用程序提供的数据。

### <a name="return-value"></a>返回值

回调函数返回**int**。此返回值是用户定义的。 如果回调函数返回 0，`EnumObjects` 将提前停止枚举。

### <a name="remarks"></a>备注

必须导出实际名称。

## <a name="graystring"></a>  Cdc:: graystring 的回调函数

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

回调函数的返回值必须为 TRUE 以指示成功;否则，它为 FALSE。

### <a name="remarks"></a>备注

回调函数 (*OutputFunc*) 必须绘制图像相对于坐标 (0，0) 而非 (*x*， *y*)。

## <a name="setabortproc"></a>  Cdc:: setabortproc 的回调函数

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
指定是否已发生错误。 如果未发生错误，则为 0。 如果，则 SP_OUTOFDISK 打印管理器目前磁盘空间不足，更多磁盘空间将变为可用如果应用程序等待。 如果*代码*是 SP_OUTOFDISK，应用程序无需中止打印作业。 如果未显示，也必须通过调用生成到打印管理器`PeekMessage`或`GetMessage`Windows 函数。

### <a name="return-value"></a>返回值

中止处理程序函数的返回值为非零，如果打印作业将继续，请和 0 如果它已取消。

### <a name="remarks"></a>备注

必须导出实际名称，如备注部分中所述[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)。

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)
