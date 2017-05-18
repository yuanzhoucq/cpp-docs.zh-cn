---
title: "CD2DRectU 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DRectU class
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
caps.latest.revision: 18
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
ms.openlocfilehash: 74c05d7f4be9b9308cdcb2b91a0455a4cd025dc1
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cd2drectu-class"></a>CD2DRectU 类
`D2D1_RECT_U`的包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DRectU : public D2D1_RECT_U;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DRectU::CD2DRectU](#cd2drectu)|已重载。 构造`CD2DRectU`对象从`D2D1_RECT_U`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DRectU::IsNull](#isnull)|返回`boolean`值，该值指示表达式是否包含无效数据 ( `null`)。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DRectU::operator CRect](#operator_crect)|将转换`CD2DRectU`到`CRect`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `D2D1_RECT_U`  
  
 `CD2DRectU`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrendertarget.h  
  
##  <a name="cd2drectu"></a>CD2DRectU::CD2DRectU  
 构造 CD2DRectU 对象从 CRect 对象。  
  
```  
CD2DRectU(const CRect& rect);  
CD2DRectU(const D2D1_RECT_U& rect);  
  CD2DRectU(const D2D1_RECT_U* rect);

 
CD2DRectU(
    UINT32 uLeft = 0,  
    UINT32 uTop = 0,  
    UINT32 uRight = 0,  
    UINT32 uBottom = 0);
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 源矩形  
  
 `uLeft`  
 源左的坐标  
  
 `uTop`  
 源上坐标  
  
 `uRight`  
 源右边坐标  
  
 `uBottom`  
 源底部坐标  
  
##  <a name="isnull"></a>CD2DRectU::IsNull  
 返回一个布尔值，该值指示表达式是否包含无效数据 (Null)。  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>返回值  
 矩形的顶部、 左边框、 下、 和正确的值完全等于 0; 如果为 TRUE否则为 FALSE。  
  
##  <a name="operator_crect"></a>CD2DRectU::operator CRect  
 将 CD2DRectU 转换成 CRect 对象。  
  
```  
operator CRect();
```   
  
### <a name="return-value"></a>返回值  
 D2D 矩形的当前值。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

