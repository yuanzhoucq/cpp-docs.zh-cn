---
title: XFORM 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- XFORM
dev_langs:
- C++
helpviewer_keywords:
- XFORM structure [MFC]
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a1c3a8abd39f7f190f36a18e7691475d951cab8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="xform-structure"></a>XFORM 结构
`XFORM`结构具有以下形式：  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct  tagXFORM {  /* xfrm */  
    FLOAT eM11;  
    FLOAT eM12;  
    FLOAT eM21;  
    FLOAT eM22;  
    FLOAT eDx;  
    FLOAT eDy;  
} XFORM;  
```  
  
## <a name="remarks"></a>备注  
 `XFORM`结构指定的页面空间转换到全局空间。 **EDx**和**eDy**成员分别指定水平和垂直转换组件。 下表显示如何使用其他成员，具体取决于该操作：  
  
|操作|eM11|eM12|eM21|eM22|  
|---------------|----------|----------|----------|----------|  
|`Rotation`|旋转角度的余弦值|旋转角度的正弦值|负的旋转角度的正弦值|旋转角度的余弦值|  
|**缩放**|水平缩放的组件|Nothing|Nothing|垂直缩放组件|  
|**切变**|Nothing|水平比例常量|垂直比例常量|Nothing|  
|**反射**|水平反射组件|Nothing|Nothing|垂直反射组件|  
  
## <a name="requirements"></a>要求  
 **标头：** wingdi.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)

