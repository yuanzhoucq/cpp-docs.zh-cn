---
title: pointer_to_unary_function 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- xfunctional/std::pointer_to_unary
dev_langs:
- C++
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5cbcad162304a4eb7750c543deac5c8e00127b2a
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function 类

将一元函数指针转换为自适应一元函数。

## <a name="syntax"></a>语法

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
public:
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>参数

`pfunc` 要转换的二元函数。

`left` 对象的 *\*pfunc*上调用。

## <a name="return-value"></a>返回值

模板类存储 **pfunc** 的副本。 它将其成员函数 `operator()` 定义为返回 (\* **pfunc**)(_ *Left*)。

## <a name="remarks"></a>备注

一元函数指针是一个函数对象，且可能会被传递到期望将一元函数作为参数的任何 C++ 标准库算法，但它不可调适。 若要将其与适配器配合使用（如向其绑定值或与求反器配合使用），则必须将其与可促成这种调适的 **argument_type** 和 **result_type** 嵌套类型一起提供。 `pointer_to_unary_function` 执行的转换允许函数适配器与二元函数指针配合使用。

## <a name="example"></a>示例

很少直接使用 `pointer_to_unary_function` 的构造函数。 有关如何声明和使用 `pointer_to_unary_function` 适配器谓词的示例，请参阅帮助程序函数 [ptr_fun](../standard-library/functional-functions.md#ptr_fun)。

## <a name="requirements"></a>要求

**标头：**\<functional>

**命名空间：** std

## <a name="see-also"></a>请参阅

[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>
