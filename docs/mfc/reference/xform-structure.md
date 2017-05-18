---
title: "XFORM 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- XFORM
dev_langs:
- C++
helpviewer_keywords:
- XFORM structure
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 2d23b3838f1e2dcabb2affb96fa6f18942581ff8
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="xform-structure"></a>XFORM 结构
`XFORM`结构具有以下形式︰  
  
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
 `XFORM`结构指定页面空间转换到世界空间。 **EDx**和**eDy**成员分别指定水平和垂直转换组件。 下表显示如何使用其他成员，具体取决于该操作︰  
  
|操作|eM11|eM12|eM21|eM22|  
|---------------|----------|----------|----------|----------|  
|`Rotation`|旋转角度的余弦值|旋转角度的正弦值|负旋转角度的正弦值|旋转角度的余弦值|  
|**缩放**|水平缩放的组件|Nothing|Nothing|垂直缩放分量|  
|**倾斜对象**|Nothing|水平比例常量|垂直比例常量|Nothing|  
|**反射**|水平反射组件|Nothing|Nothing|垂直反射组件|  
  
## <a name="requirements"></a>要求  
 **标头︰** wingdi.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)


