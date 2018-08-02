---
title: ComPtr::Reset |Microsoft Docs
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
ms.openlocfilehash: 6edbe333ddb634d8657712695250ec627a171780
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461079"
---
# <a name="comptrreset"></a>ComPtr::Reset
释放对与此相关联的接口指针的所有引用**ComPtr**。  
  
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