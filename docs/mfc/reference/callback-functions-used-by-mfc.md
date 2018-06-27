---
title: MFC 使用的回调函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.functions
dev_langs:
- C++
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 114411d0f8c7084e26f36f0ffc05e60a32407c44
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956829"
---
# <a name="callback-functions-used-by-mfc"></a>MFC 使用的回调函数
在 Microsoft 基础类库中显示三个回调函数。 这些回调函数传递给[cdc:: enumobjects](../../mfc/reference/cdc-class.md#enumobjects)， [cdc:: graystring](../../mfc/reference/cdc-class.md#graystring)，和[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)。 请注意所有回调函数必须都捕获返回到 Windows，因为不能跨回调边界引发异常之前的 MFC 异常。 有关异常的详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  

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
 *lpszLogObject*  
 指向[LOGPEN](../../mfc/reference/logpen-structure.md)或[LOGBRUSH](../../mfc/reference/logbrush-structure.md)数据结构，其中包含有关的逻辑特性的对象的信息。  
  
 *lpData*  
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
 *hDC*  
 标识内存设备上下文与至少包含位图的宽度和高度指定*nWidth*和*nHeight*到`GrayString`。  
  
 *lpData*  
 指向要绘制的字符串。  
  
 *nCount*  
 指定要输出的字符数。  
  
### <a name="return-value"></a>返回值  
 回调函数的返回值必须是**TRUE**以指示成功; 否则它是**FALSE**。  
  
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
 *hPr*  
 标识设备上下文。  
  
 *代码*  
 指定是否已发生了错误。 如果未发生错误，则为 0。 它是**SP_OUTOFDISK**如果打印管理器当前磁盘空间不足，更多磁盘空间将变为可用，如果应用程序在等待。 如果*代码*是**SP_OUTOFDISK**，应用程序没有中止打印作业。 如果不存在，也必须通过调用生成到打印管理器`PeekMessage`或`GetMessage`Windows 函数。  
  
### <a name="return-value"></a>返回值  
 中止处理程序函数的返回值表示打印作业是否要继续，则为非 0，0 如果它被取消。  
  
### <a name="remarks"></a>备注  
 中的备注部分所述，必须导出实际名称[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)。  
 
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](structures-styles-callbacks-and-message-maps.md) [cdc:: enumobjects](../../mfc/reference/cdc-class.md#enumobjects) [cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc) [cdc:: graystring](../../mfc/reference/cdc-class.md#graystring)

