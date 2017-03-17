---
title: "CD2DSizeU 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::CD2DSizeU
- AFXRENDERTARGET/CD2DSizeU::IsNull
dev_langs:
- C++
helpviewer_keywords:
- CD2DSizeU class
ms.assetid: 6e679ba8-2112-43c3-8275-70b660856f02
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
ms.openlocfilehash: a43ea5448a0b0d09d4cf27eafb01a4d4b610e4f5
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dsizeu-class"></a>CD2DSizeU 类
D2D1_SIZE_U 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DSizeU : public D2D1_SIZE_U;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DSizeU::CD2DSizeU](#cd2dsizeu)|已重载。 构造`CD2DSizeU`对象从`D2D1_SIZE_U`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DSizeU::IsNull](#isnull)|返回`boolean`值，该值指示表达式是否包含无效数据 ( `null`)。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DSizeU::operator CSize](#operator_csize)|将转换`CD2DSizeU`到`CSize`对象。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `D2D1_SIZE_U`  
  
 [CD2DSizeU](../../mfc/reference/cd2dsizeu-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrendertarget.h  
  
##  <a name="cd2dsizeu"></a>CD2DSizeU::CD2DSizeU  
 构造 CD2DSizeU 对象从 CSize 对象。  
  
```  
CD2DSizeU(const CSize& size);  
CD2DSizeU(const D2D1_SIZE_U& size);  
  CD2DSizeU(const D2D1_SIZE_U* size);

 
CD2DSizeU(
    UINT32 cx = 0,  
    UINT32 cy = 0);
```  
  
### <a name="parameters"></a>参数  
 `size`  
 源的大小  
  
 `cx`  
 源宽度  
  
 `cy`  
 源高度  
  
##  <a name="isnull"></a>CD2DSizeU::IsNull  
 返回一个布尔值，该值指示表达式是否包含无效数据 (Null)。  
  
```  
BOOL IsNull() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果宽度和高度都为空;，则返回 TRUE否则为 FALSE。  
  
##  <a name="operator_csize"></a>CD2DSizeU::operator CSize  
 将 CD2DSizeU 转换成 CSize 对象。  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>返回值  
 D2D 大小的当前值。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

