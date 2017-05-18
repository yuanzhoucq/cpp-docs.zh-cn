---
title: "MFC 使用的回调函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.functions
dev_langs:
- C++
helpviewer_keywords:
- callback functions, MFC
- MFC, callback functions
- functions [C++], callback
- callback functions
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: d4b97ed874b145f9c6d9a9536476243bba0fd1c1
ms.openlocfilehash: 08c6f547c95adb4c6794ec71259888d390e42e92
ms.contentlocale: zh-cn
ms.lasthandoff: 03/06/2017

---
# <a name="callback-functions-used-by-mfc"></a>MFC 使用的回调函数
在 Microsoft 基础类库中显示三个回调函数。 这些回调函数传递给[cdc:: enumobjects](../../mfc/reference/cdc-class.md#enumobjects)， [cdc:: graystring](../../mfc/reference/cdc-class.md#graystring)，和[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)。 请注意所有的回调函数必须捕获返回到 Windows 帐户，因为不能跨回调边界引发异常之前的 MFC 异常。 关于异常的详细信息，请参阅文章[异常](../../mfc/exception-handling-in-mfc.md)。  

|名称||  
|----------|-----------------|  
|[CDC::EnumObjects 的回调函数](#enum_objects)||  
|[CDC::GrayString 的回调函数](#graystring)||
|[Callback Function for CDC::SetAbortProc](#setabortproc)|| 

## <a name="requirements"></a>要求  
 **标头:** afxwin.h 

## <a name="enum_objects"></a>Cdc:: enumobjects 的回调函数
*ObjectFunc*名称是应用程序提供的函数名称的占位符。  
  
### <a name="syntax"></a>语法  
  
```  
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,  
    LPSTR* lpData);
```  
  
### <a name="parameters"></a>参数  
 *lpszLogObject*  
 指向[LOGPEN](../../mfc/reference/logpen-structure.md)或[LOGBRUSH](../../mfc/reference/logbrush-structure.md)数据结构，其中包含的对象的逻辑特性信息。  
  
 `lpData`  
 指向传递给 `EnumObjects` 函数的应用程序提供的数据。  
  
### <a name="return-value"></a>返回值  
 回调函数返回 `int`。 此返回值是用户定义的。 如果回调函数返回 0，`EnumObjects` 将提前停止枚举。  
  
### <a name="remarks"></a>备注  
 必须导出实际名称。  
  
## <a name="graystring"></a>Cdc:: graystring 的回调函数
*OutputFunc*是由应用程序提供的回调函数名称的占位符。  
  
### <a name="syntax"></a>语法  
  
```  
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,  
    LPARAM lpData,  
    int nCount);
```  
  
### <a name="parameters"></a>参数  
 `hDC`  
 向 `nWidth` 标识一个内存设备上下文，该上下文具有宽度和高度至少为 `nHeight` 和 `GrayString` 指定的值的位图。  
  
 `lpData`  
 指向要绘制的字符串。  
  
 `nCount`  
 指定要输出的字符数。  
  
### <a name="return-value"></a>返回值  
 回调函数的返回值必须是**TRUE**以指示成功; 否则它就是**FALSE**。  
  
### <a name="remarks"></a>备注  
 回调函数 (*OutputFunc*) 必须绘制的图像相对于坐标 (0，0) 而不是 (*x*， *y*)。  

## <a name="setabortproc"></a>Cdc:: setabortproc 的回调函数
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
  
 `code`  
 指定是否已发生了错误。 如果未发生错误，则为 0。 它是**SP_OUTOFDISK**如果打印管理器当前磁盘空间不足，更多磁盘空间将变为可用，如果应用程序等待。 如果`code`是**SP_OUTOFDISK**，应用程序没有中止打印作业。 如果不存在，它必须通过调用产生到打印管理器**PeekMessage**或**GetMessage** Windows 函数。  
  
### <a name="return-value"></a>返回值  
 终止处理程序函数的返回值，并且如果打印作业若要继续，则为非 0 如果就被取消。  
  
### <a name="remarks"></a>备注  
 中的备注部分所述，必须导出实际名称[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)。  
 
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](structures-styles-callbacks-and-message-maps.md)
 [cdc:: enumobjects](../../mfc/reference/cdc-class.md#enumobjects)
 [cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)
 [cdc:: graystring](../../mfc/reference/cdc-class.md#graystring)


