---
title: "Safeint:: Safeint |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeInt::SafeInt
- SafeInt
- SafeInt.SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class, constructor
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a9820227384866cdb1a6470ebd9650187848334c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="safeintsafeint"></a>SafeInt::SafeInt
构造 `SafeInt` 对象。  
  
## <a name="syntax"></a>语法  
  
```  
SafeInt() throw  
  
SafeInt (  
   const T& i  
) throw ()  
  
SafeInt (  
   bool b  
) throw ()  
  
template <typename U>  
SafeInt (  
   const SafeInt <U, E>& u  
)  
  
I template <typename U>  
SafeInt (  
   const U& i  
)  
```  
  
#### <a name="parameters"></a>参数  
 [in] `i`  
 新值`SafeInt`对象。 这必须是类型 T 或 U，具体取决于构造函数的参数。  
  
 [in] `b`  
 新的布尔值`SafeInt`对象。  
  
 [in] `u`  
 A`SafeInt`类型 u。新`SafeInt`对象将具有相同的值`u`，但将类型为 t。  
  
 U  
 中存储的数据类型`SafeInt`。 这可以是布尔值、 字符或整数类型。 如果它是整数类型，可以对其签名或未签名，而且之间 8 和 64 位。  
  
## <a name="remarks"></a>备注  
 有关模板类型的详细信息`T`和`E`，请参阅[SafeInt 类](../windows/safeint-class.md)。  
  
 构造函数中，输入的参数`i`或`u`，必须是布尔值、 字符或整数类型。 如果它是另一个类型的参数，`SafeInt`类调用[static_assert](../cpp/static-assert.md)以指示输入的参数无效。  
  
 使用模板类型的构造函数`U`自动将输入的参数转换为指定的类型`T`。 `SafeInt`类将不会丢失任何数据的数据转换。 向错误处理程序报告`E`如果它无法转换数据以键入`T`而不丢失数据。  
  
 如果你创建`SafeInt`从一个布尔型参数，您需要立即初始化值。 无法构造`SafeInt`使用代码`SafeInt<bool> sb;`。 这将生成一个编译错误。  
  
## <a name="requirements"></a>惠?  
 **标头：** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>请参阅  
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeInt 类](../windows/safeint-class.md)   
 [SafeIntException 类](../windows/safeintexception-class.md)