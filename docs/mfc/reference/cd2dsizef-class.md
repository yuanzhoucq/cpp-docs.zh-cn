---
title: CD2DSizeF 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::CD2DSizeF
- AFXRENDERTARGET/CD2DSizeF::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeF [MFC], CD2DSizeF
- CD2DSizeF [MFC], IsNull
ms.assetid: f486a1e1-997d-4286-8cb9-26369dc82055
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0093c92604013e4c1aef4046f244d7bcd3f71958
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353320"
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
|[CD2DSizeF::CD2DSizeF](#cd2dsizef)|已重载。 构造`CD2DSizeF`对象`D2D1_SIZE_F`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DSizeF::IsNull](#isnull)|返回`boolean`值，该值指示表达式是否包含任何有效的数据 ( `null`)。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DSizeF::operator CSize](#operator_csize)|将转换`CD2DSizeF`到`CSize`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `D2D1_SIZE_F`  
  
 [CD2DSizeF](../../mfc/reference/cd2dsizef-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxrendertarget.h  
  
##  <a name="cd2dsizef"></a>  CD2DSizeF::CD2DSizeF  
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
  
##  <a name="isnull"></a>  CD2DSizeF::IsNull  
 返回一个布尔值，该值指示表达式是否包含任何有效的数据 (Null)。  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>返回值  
 宽度和高度都为空; 如果为 TRUE否则为 FALSE。  
  
##  <a name="operator_csize"></a>  CD2DSizeF::operator CSize  
 将 CD2DSizeF 转换 CSize 对象。  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>返回值  
 D2D 大小的当前值。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
