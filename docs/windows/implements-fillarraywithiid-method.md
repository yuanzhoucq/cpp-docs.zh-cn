---
title: 'Implements:: fillarraywithiid 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: b2e62e3f-0ab9-4c70-aad7-856268544f44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e020bd725d0c0f5c65ab1cfb38b45e2b8fbca62e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875716"
---
# <a name="implementsfillarraywithiid-method"></a>Implements::FillArrayWithIid 方法
将插入到指定的数组元素指定由当前第零个模板参数的接口 ID。  
  
## <a name="syntax"></a>语法  
  
```  
__forceinline static void FillArrayWithIid(  
   unsigned long &index,  
   _In_ IID* iids  
);  
```  
  
#### <a name="parameters"></a>参数  
 `index`  
 一个指示此操作开始的数组元素的从零开始索引。 此操作完成后，`index`就会递增 1。  
  
 `iids`  
 类型 IID 的数组。  
  
## <a name="remarks"></a>备注  
 内部帮助程序函数。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Implements 结构](../windows/implements-structure.md)