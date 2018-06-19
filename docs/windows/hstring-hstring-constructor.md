---
title: 'Hstring:: Hstring 构造函数 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs:
- C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3188e137d3a39fb26ca4151f72073306038e46f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876873"
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
  
## <a name="see-also"></a>请参阅  
 [HString 类](../windows/hstring-class.md)