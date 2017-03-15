---
title: "COLORADJUSTMENT 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- COLORADJUSTMENT
dev_langs:
- C++
helpviewer_keywords:
- COLORADJUSTMENT structure
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
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
ms.openlocfilehash: 7f88877fa009abf4e811ba0a99b7e0e1683f998a
ms.lasthandoff: 02/24/2017

---
# <a name="coloradjustment-structure"></a>COLORADJUSTMENT 结构
`COLORADJUSTMENT`结构定义 Windows 所使用的颜色调整值`StretchBlt`和**StretchDIBits**函数时`StretchBlt`模式是**半色调**。  
  
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
 指定输出图像应做好准备。 此成员可以将设置为**NULL**或以下值的任意组合︰  
  
- **CA_NEGATIVE**指定应显示原始图像的负值。  
  
- **CA_LOG_FILTER**指定对数函数，应该应用于最终输出颜色的密度。 亮度较低时，这将增加的色彩对比度。  
  
 *caIlluminantIndex*  
 指定在其下查看 image 对象的光源的亮度。 此成员可以设置为下列值之一︰  
  
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
 指定源颜色的红色主的 n 次幂灰度校正值。 值必须介于 2500 65000。 值为 10000 意味着没有灰度校正。  
  
 *caGreenGamma*  
 指定源颜色的绿色主的 n 次幂灰度校正值。 值必须介于 2500 65000。 值为 10000 意味着没有灰度校正。  
  
 *caBlueGamma*  
 指定源颜色蓝原色的 n 次幂灰度校正值。 值必须介于 2500 65000。 值为 10000 意味着没有灰度校正。  
  
 *caReferenceBlack*  
 指定源颜色为黑色的引用。 这比暗的任何颜色将被视为黑色。 值必须介于 0 到 4000。  
  
 *caReferenceWhite*  
 指定源色为白色的引用。 这比亮的任何颜色将被视为空白。 值必须在范围从 6000 到 10000。  
  
 *caContrast*  
 指定要应用于源对象的对比度的量。 值必须为介于-100 到 100 之间。 值为 0 表示没有对比度调整。  
  
 *caBrightness*  
 指定的量亮度，以将应用于源对象。 值必须为介于-100 到 100 之间。 值为 0 表示无亮度调整。  
  
 *caColorfulness*  
 指定要应用于源对象的 colorfulness 量。 值必须为介于-100 到 100 之间。 值为 0 表示未 colorfulness 进行调整。  
  
 *caRedGreenTint*  
 指定要应用于源对象的红色或绿色色调调整量。 值必须为介于-100 到 100 之间。 为正的数字将以红色调整并负数调整朝向绿色。 0 表示未进行色调调整。  
  
## <a name="requirements"></a>要求  
 **标头︰** wingdi.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)



