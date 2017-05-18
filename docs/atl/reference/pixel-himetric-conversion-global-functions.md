---
title: "像素 HIMETRIC 转换全局函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
caps.latest.revision: 19
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: efb7e7da896aea4e377225f4c1e2c9948e635705
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="pixelhimetric-conversion-global-functions"></a>像素/HIMETRIC 转换全局函数
这些函数为像素和 himetric 为单位来回转换提供支持。  
  
> [!IMPORTANT]
>  下表中列出的函数不能用于应用程序中执行[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
|||  
|-|-|  
|[AtlHiMetricToPixel](#atlhimetrictopixel)|将 himetric 为单位 （每个单位是 0.01 毫米） 转换为像素。|  
|[AtlPixelToHiMetric](#atlpixeltohimetric)|将像素转换为 himetric 为单位 （每个单位是 0.01 毫米）。|  
  
##  <a name="atlhimetrictopixel"></a>AtlHiMetricToPixel  
 将以 HIMETRIC 为单位（每个单位是 0.01 毫米）的对象大小转换为以屏幕设备上的像素为单位的大小。  
  
 
```
extern void AtlHiMetricToPixel(
  const SIZEL* lpSizeInHiMetric, 
  LPSIZEL lpSizeInPix);
```  
  
### <a name="parameters"></a>参数  
 `lpSizeInHiMetric`  
 [in]为以 himetric 为单位的对象的大小的指针。  
  
 `lpSizeInPix`  
 [out]到的位置以像素为单位的对象的大小要返回的指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#49;](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]  

### <a name="requirements"></a>要求  
 **标头︰** atlwin.h  
  
##  <a name="atlpixeltohimetric"></a>AtlPixelToHiMetric  
 将以屏幕设备上的像素为单位的对象大小转换为以 HIMETRIC 为单位（每个单位是 0.01 毫米）的大小。  
  
```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix, 
    LPSIZEL lpSizeInHiMetric);
```  
  
### <a name="parameters"></a>参数  
 `lpSizeInPix`  
 [in]指针指向对象的大小，以像素为单位。  
  
 `lpSizeInHiMetric`  
 [out]到的位置以 himetric 为单位的对象的大小要返回的指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#51;](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]  

### <a name="requirements"></a>要求  
 **标头︰** atlwin.h  

## <a name="see-also"></a>另请参阅  
 [函数](../../atl/reference/atl-functions.md)

