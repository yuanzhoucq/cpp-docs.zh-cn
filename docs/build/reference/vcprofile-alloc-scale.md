---
title: "VCPROFILE_ALLOC_SCALE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VCPROFILE_ALLOC_SCALE
dev_langs:
- C++
helpviewer_keywords:
- VCPROFILE_ALLOC_SCALE environment variable
ms.assetid: 5cb5ce27-f9b8-489b-b46c-d6e9bcab2d34
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7b441f41106544633bd691c409fa04c989146f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE
修改分配以保存配置文件数据的内存量。  
  
## <a name="syntax"></a>语法  
  
```  
VCPROFILE_ALLOC_SCALE=scale_value  
```  
  
#### <a name="parameters"></a>参数  
 `scale_value`  
 用于运行测试方案所需的内存量的范围值。  默认值为 1。  
  
## <a name="remarks"></a>备注  
 在极少数情况下，将不会有足够的内存可用于支持运行测试方案时收集配置文件数据。  在这些情况下，你可以增加使用的内存量`VCPROFILE_ALLOC_SCALE`。  
  
 如果测试运行，该值指示你没有足够的内存期间收到一条错误消息，将分配到更大的值`VCPROFILE_ALLOC_SCALE`，直到在测试运行完成，但没有内存不足错误。  
  
## <a name="example"></a>示例  
  
```  
set VCPROFILE_ALLOC_SCALE=2  
```  
  
## <a name="see-also"></a>请参阅  
 [用于按配置文件优化的环境变量](../../build/reference/environment-variables-for-profile-guided-optimizations.md)