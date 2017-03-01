---
title: "CD2DSizeF 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxrendertarget/CD2DSizeF
- CD2DSizeF
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeF class
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f780dc919f102023f2bd524fa69e73e76feec02b
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dsizef-class"></a>CD2DSizeF 类
D2D1_SIZE_F 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DSizeF : public D2D1_SIZE_F;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|已重载。 构造`CD2DSizeF`对象从`D2D1_SIZE_F`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DSizeF::IsNull](#isnull)|返回`boolean`值，该值指示表达式是否包含无效数据 ( `null`)。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DSizeF::operator CSize](#operator_csize)|将转换`CD2DSizeF`到`CSize`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `D2D1_SIZE_F`  
  
 [CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrendertarget.h  
  
##  <a name="a-namecd2dsizefa--cd2dsizefcd2dsizef"></a><a name="cd2dsizef"></a>CD2DSizeF::CD2DSizeF  
 构造 CD2DSizeF 对象从 CSize 对象。  
  
```  
CD2DSizeF(const CSize& size);  
CD2DSizeF(const D2D1_SIZE_F& size);  
  CD2DSizeF(const D2D1_SIZE_F* size);

 
CD2DSizeF(
    FLOAT cx = 0.,  
    FLOAT cy = 0.);
```  
  
### <a name="parameters"></a>参数  
 `size`  
 源的大小  
  
 `cx`  
 源宽度  
  
 `cy`  
 源高度  
  
##  <a name="a-nameisnulla--cd2dsizefisnull"></a><a name="isnull"></a>CD2DSizeF::IsNull  
 返回一个布尔值，该值指示表达式是否包含无效数据 (Null)。  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果宽度和高度都为空;，则返回 TRUE否则为 FALSE。  
  
##  <a name="a-nameoperatorcsizea--cd2dsizefoperator-csize"></a><a name="operator_csize"></a>CD2DSizeF::operator CSize  
 将 CD2DSizeF 转换成 CSize 对象。  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>返回值  
 D2D 大小的当前值。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

