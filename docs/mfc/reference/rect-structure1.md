---
title: RECT 结构 1 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LPRECT
- RECT
dev_langs:
- C++
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b61c794b8fa383eeea62459a5a83948ef2efe10
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="rect-structure1"></a>RECT 结构 1
`RECT` 结构定义矩形左上角和右下角的坐标。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagRECT {  
    LONG left;  
    LONG top;  
    LONG right;  
    LONG bottom;  
} RECT;  
```  
  
## <a name="members"></a>成员  
 `left`  
 指定矩形左上角的 x 坐标。  
  
 `top`  
 指定矩形左上角的 y 坐标。  
  
 `right`  
 指定矩形右下角的 x 坐标。  
  
 `bottom`  
 指定矩形右下角的 y 坐标。  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头：** windef.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRect 类](../../atl-mfc-shared/reference/crect-class.md)
