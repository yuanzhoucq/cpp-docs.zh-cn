---
title: "ABC 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ABC
dev_langs: C++
helpviewer_keywords: ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ba8add08fcd5ff3d7343477aafa7d910885b0b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="abc-structure"></a>ABC 结构
**ABC**结构包含 TrueType 字体中字符的宽度。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _ABC { /* abc */  
    int abcA;  
    UINT abcB;  
    int abcC;  
} ABC;  
```  
  
#### <a name="parameters"></a>参数  
 *abcA*  
 指定字符的 A 间距。 A 间距是在绘制字符标志符号之前要添加到当前位置的距离。  
  
 *abcB*  
 指定字符的 B 间距。 B 间距是字符标志符号的绘制部分的宽度。  
  
 *abcC*  
 指定字符的 C 间距。 C 间距是要添加到当前位置以便为字符标志符号的右侧提供空白的距离。  
  
## <a name="remarks"></a>备注  
 字符的整个宽度为 A、B 和 C 间距的总和。 A 或 C 间距可以是负值以指示空白部分或延伸量。  
  
## <a name="requirements"></a>惠?  
 **标头：** wingdi.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


