---
title: "ABCFLOAT 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ABCFLOAT
dev_langs: C++
helpviewer_keywords: ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b58871df5a526455297dd6d092f98e9facd901ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="abcfloat-structure"></a>ABCFLOAT 结构
`ABCFLOAT`结构包含字体字符 A、 B 和 C 宽度。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct _ABCFLOAT { /* abcf */  
    FLOAT abcfA;  
    FLOAT abcfB;  
    FLOAT abcfC;  
} ABCFLOAT;  
```  
  
#### <a name="parameters"></a>参数  
 *abcfA*  
 指定字符的 A 间距。 A 间距是在绘制字符标志符号之前要添加到当前位置的距离。  
  
 *abcfB*  
 指定字符的 B 间距。 B 间距是字符标志符号的绘制部分的宽度。  
  
 *abcfC*  
 指定字符的 C 间距。 C 间距是要添加到当前位置以便为字符标志符号的右侧提供空白的距离。  
  
## <a name="remarks"></a>备注  
 A、 B 和 C 宽度测量沿字体的基线。 字符增量 （总宽度） 的一个字符是 A、 B 和 C 空间之和。 A 或 C 间距可以是负值以指示空白部分或延伸量。  
  
## <a name="requirements"></a>惠?  
 **标头：** wingdi.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

