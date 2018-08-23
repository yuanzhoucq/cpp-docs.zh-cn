---
title: ABC 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABC
dev_langs:
- C++
helpviewer_keywords:
- ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c9aac181edb12df8904a2bc6d891d59c0067ecc
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339314"
---
# <a name="abc-structure"></a>ABC 结构
`ABC`结构包含 TrueType 字体中字符的宽度。  
  
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
  
## <a name="requirements"></a>要求  
 **标头：** wingdi.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


