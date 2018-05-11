---
title: ComPtr::Reset |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: aa6a46f7-f56b-4fd5-add0-7cea55f7abda
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd2ce820367b15cb5dad8baf691a835499457a55
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="comptrreset"></a>ComPtr::Reset
释放所有指向与此 ComPtr 相关联的接口的指针的引用。  
  
## <a name="syntax"></a>语法  
  
```  
unsigned long Reset();  
```  
  
## <a name="return-value"></a>返回值  
 已释放的引用的数量（如果存在）。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ComPtr 类](../windows/comptr-class.md)