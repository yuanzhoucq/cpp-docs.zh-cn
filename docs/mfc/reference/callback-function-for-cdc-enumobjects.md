---
title: "Cdc:: enumobjects 的回调函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Callback Function for CDC::EnumObjects
dev_langs:
- C++
helpviewer_keywords:
- callback functions, for CDC::EnumObjects
ms.assetid: 380088b1-88a5-4fb4-bbb5-dd9e8386572b
caps.latest.revision: 10
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
ms.openlocfilehash: e4b24b5f5333d5514b9fdf69d204bca5d7947d7a
ms.lasthandoff: 02/24/2017

---
# <a name="callback-function-for-cdcenumobjects"></a>CDC::EnumObjects 的回调函数
*ObjectFunc*名称是应用程序提供的函数名称的占位符。  
  
## <a name="syntax"></a>语法  
  
```  
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,  
    LPSTR* lpData);
```  
  
#### <a name="parameters"></a>参数  
 *lpszLogObject*  
 指向[LOGPEN](../../mfc/reference/logpen-structure.md)或[LOGBRUSH](../../mfc/reference/logbrush-structure.md)数据结构，其中包含的对象的逻辑特性信息。  
  
 `lpData`  
 指向传递给 `EnumObjects` 函数的应用程序提供的数据。  
  
## <a name="return-value"></a>返回值  
 回调函数返回 `int`。 此返回值是用户定义的。 如果回调函数返回 0，`EnumObjects` 将提前停止枚举。  
  
## <a name="remarks"></a>备注  
 必须导出实际名称。  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Cdc:: enumobjects](../../mfc/reference/cdc-class.md#enumobjects)


