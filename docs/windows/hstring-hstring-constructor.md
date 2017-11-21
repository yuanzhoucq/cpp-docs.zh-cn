---
title: "Hstring:: Hstring 构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs: C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a598b6a4b0e1b6077e2232131814192ef0a81863
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="hstringhstring-constructor"></a>HString::HString 构造函数
初始化 HString 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `hstr`  
 HSTRING 句柄。  
  
 `other`  
 现有 HString 对象。  
  
## <a name="remarks"></a>备注  
 第一个构造函数初始化为空的新 HString 对象。  
  
 第二个构造函数初始化的现有值将新 HString 对象`other`参数，然后销毁`other`参数。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另请参阅  
 [HString 类](../windows/hstring-class.md)