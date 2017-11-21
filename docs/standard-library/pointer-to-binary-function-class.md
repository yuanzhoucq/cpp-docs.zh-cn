---
title: "pointer_to_binary_function 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::pointer_to_binary
dev_langs: C++
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 70c9d0a54976e8aa69175a730b1fcc747065d849
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="pointertobinaryfunction-class"></a>pointer_to_binary_function 类
将二元函数指针转换为自适应二元函数。  
  
## <a name="syntax"></a>语法  
  
```
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
public:
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```  
  
#### <a name="parameters"></a>参数  
 `pfunc`  
 要转换的二元函数。  
  
 `left`  
 对其调用 *\*pfunc* 的左侧对象。  
  
 `right`  
 对其调用 *\*pfunc* 的右侧对象。  
  
## <a name="return-value"></a>返回值  
 模板类存储 **pfunc** 的副本。 它将其成员函数 `operator()` 定义为返回 (\* **pfunc**)(_ *Left*, \_ *Right*)。  
  
## <a name="remarks"></a>备注  
 二元函数指针是一个函数对象，且可能会被传递到期望将二元函数作为参数的任何 C++ 标准库算法，但这不适用。 若要将其与适配器配合使用（如向其绑定值或与求反器配合使用），则必须将其与可使这种适应成为可能的 **first_argument_type**、**second_argument_type** 和 **result_type** 嵌套类型一起提供。 `pointer_to_binary_function` 执行的转换允许函数适配器与二元函数指针配合使用。  
  
## <a name="example"></a>示例  
 很少直接使用 `pointer_to_binary_function` 的构造函数。 有关如何声明和使用 `pointer_to_binary_function` 适配器谓词的示例，请参阅帮助程序函数 [ptr_fun](../standard-library/functional-functions.md#ptr_fun)。  
  
## <a name="requirements"></a>要求  
 **标头：**\<functional>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)



