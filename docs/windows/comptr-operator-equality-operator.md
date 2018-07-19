---
title: 'Comptr:: Operator = = 运算符 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator==
dev_langs:
- C++
ms.assetid: 6a26e936-29d4-4b7d-b44a-7c575ad07509
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 703204541a05c260e77562729703677b98fb8e9d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883350"
---
# <a name="comptroperator-operator"></a>ComPtr::operator== 运算符
指示两个 ComPtr 对象是否相等。  
  
## <a name="syntax"></a>语法  
  
```cpp  
bool operator==(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator==(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const ComPtr<T>& a  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 `a`  
 对的 ComPtr 对象的引用。  
  
 `b`  
 对另一个 ComPtr 对象的引用。  
  
## <a name="return-value"></a>返回值  
 第一个运算符生成`true`如果对象`a`是否等于对象`b`; 否则为`false`。  
  
 第二个和第三个运算符生成`true`如果对象`a`等同于`nullptr`; 否则为`false`。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft:: wrl Namespace](../windows/microsoft-wrl-namespace.md)   
 [ComPtr 类](../windows/comptr-class.md)