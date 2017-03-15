---
title: "Cdc:: graystring 的回调函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Callback Function for CDC::GrayString
dev_langs:
- C++
helpviewer_keywords:
- callback functions, for CDC::GrayString
ms.assetid: 5217e183-df48-426b-931b-6245022ca36f
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 3ce3afefae9618420a8a97b27994c33604745677
ms.lasthandoff: 02/24/2017

---
# <a name="callback-function-for-cdcgraystring"></a>CDC::GrayString 的回调函数
*OutputFunc*是由应用程序提供的回调函数名称的占位符。  
  
## <a name="syntax"></a>语法  
  
```  
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,  
    LPARAM lpData,  
    int nCount);
```  
  
#### <a name="parameters"></a>参数  
 `hDC`  
 向 `nWidth` 标识一个内存设备上下文，该上下文具有宽度和高度至少为 `nHeight` 和 `GrayString` 指定的值的位图。  
  
 `lpData`  
 指向要绘制的字符串。  
  
 `nCount`  
 指定要输出的字符数。  
  
## <a name="return-value"></a>返回值  
 回调函数的返回值必须是**TRUE**以指示成功; 否则它就是**FALSE**。  
  
## <a name="remarks"></a>备注  
 回调函数 (*OutputFunc*) 必须绘制的图像相对于坐标 (0，0) 而不是 (*x*， *y*)。  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Cdc:: graystring](../../mfc/reference/cdc-class.md#graystring)


