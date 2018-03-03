---
title: "COLORADJUSTMENT 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- COLORADJUSTMENT
dev_langs:
- C++
helpviewer_keywords:
- COLORADJUSTMENT structure [MFC]
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b4e86010cda3545a6216767c1519bc5b2bccdf43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="coloradjustment-structure"></a>COLORADJUSTMENT 结构
`COLORADJUSTMENT`结构定义使用 Windows 的颜色调整值`StretchBlt`和**StretchDIBits**函数时`StretchBlt`模式是**半色调**。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct  tagCOLORADJUSTMENT {    /* ca */  
    WORD caSize;  
    WORD caFlags;  
    WORD caIlluminantIndex;  
    WORD caRedGamma;  
    WORD caGreenGamma;  
    WORD caBlueGamma;  
    WORD caReferenceBlack;  
    WORD caReferenceWhite;  
    SHORT caContrast;  
    SHORT caBrightness;  
    SHORT caColorfulness;  
    SHORT caRedGreenTint;  
} COLORADJUSTMENT;  
```  
  
#### <a name="parameters"></a>参数  
 *caSize*  
 以字节为单位指定结构的大小。  
  
 *caFlags*  
 指定应如何准备输出图像。 此成员可以将设置为**NULL**或以下值的任意组合：  
  
- **CA_NEGATIVE**指定应显示原始图像的负值。  
  
- **CA_LOG_FILTER**指定对数函数，应应用于最终输出颜色的密度。 亮度较低时，这将增加的颜色对比度。  
  
 *caIlluminantIndex*  
 指定在其下查看图像对象的光源的亮度。 此成员可以设置为以下值之一：  
  
- **ILLUMINANT_EQUAL_ENERGY**  
  
- **ILLUMINANT_A**  
  
- **ILLUMINANT_B**  
  
- **ILLUMINANT_C**  
  
- **ILLUMINANT_D50**  
  
- **ILLUMINANT_D55**  
  
- **ILLUMINANT_D65**  
  
- **ILLUMINANT_D75**  
  
- **ILLUMINANT_F2**  
  
- **ILLUMINANT_TURNGSTEN**  
  
- **ILLUMINANT_DAYLIGHT**  
  
- **ILLUMINANT_FLUORESCENT**  
  
- **ILLUMINANT_NTSC**  
  
 *caRedGamma*  
 指定的源颜色的红色的主 n 次幂灰度校正值。 值必须介于 2500 65000。 值为 10000 表示没有灰度校正。  
  
 *caGreenGamma*  
 指定的源颜色的绿色的主 n 次幂灰度校正值。 值必须介于 2500 65000。 值为 10000 表示没有灰度校正。  
  
 *caBlueGamma*  
 指定的源颜色的蓝色的主 n 次幂灰度校正值。 值必须介于 2500 65000。 值为 10000 表示没有灰度校正。  
  
 *caReferenceBlack*  
 指定源颜色的黑色的引用。 任何比这更深的颜色将被视为黑色。 值必须介于 0 到 4000。  
  
 *caReferenceWhite*  
 指定源颜色的白色的引用。 这比亮任何颜色将被视为空白。 值必须为范围从 6000 到 10,000。  
  
 *caContrast*  
 指定要应用到源对象的对比度量。 值必须在 100 到-100 范围内。 值为 0 表示未对比度进行调整。  
  
 *caBrightness*  
 指定的量亮度，以应用于源对象。 值必须在 100 到-100 范围内。 值为 0 表示未亮度进行调整。  
  
 *caColorfulness*  
 指定的量 colorfulness 要应用到源对象。 值必须在 100 到-100 范围内。 值为 0 表示未 colorfulness 进行调整。  
  
 *caRedGreenTint*  
 指定要应用到源对象的红色或绿色浅色调整量。 值必须在 100 到-100 范围内。 正数会调整朝向红色并负数调整朝向绿色。 0 表示未浅色进行调整。  
  
## <a name="requirements"></a>惠?  
 **标头：** wingdi.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)


