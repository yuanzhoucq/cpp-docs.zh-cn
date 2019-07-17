---
title: pointer_to_unary_function 类
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: cff84f1f15eea34c60162f702dfe05350d1383d1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240466"
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function 类

将一元函数指针转换为自适应一元函数。 在 C + + 11 中，在 C + + 17 中删除不推荐使用。

## <a name="syntax"></a>语法

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>参数

*pfunc*\
要转换的二元函数。

*左侧*\
在其上调用 *\*pfunc* 的对象。

## <a name="return-value"></a>返回值

此模板类存储一份`pfunc`。 它将其成员函数 `operator()` 定义为返回 (\* **pfunc**)(_ *Left*)。

## <a name="remarks"></a>备注

一元函数指针是一个函数对象，且可能会被传递到期望将一元函数作为参数的任何 C++ 标准库算法，但它不可调适。 若要使用与适配器，如向其绑定值或将它与配合，它必须提供嵌套类型一起`argument_type`和`result_type`，使这种适应成为可能。 `pointer_to_unary_function` 执行的转换允许函数适配器与二元函数指针配合使用。

## <a name="example"></a>示例

很少直接使用 `pointer_to_unary_function` 的构造函数。 有关如何声明和使用 `pointer_to_unary_function` 适配器谓词的示例，请参阅帮助程序函数 [ptr_fun](../standard-library/functional-functions.md#ptr_fun)。
