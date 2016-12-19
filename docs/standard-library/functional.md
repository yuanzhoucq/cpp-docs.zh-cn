---
title: "&lt; 功能 &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<functional>"
  - "functional/std::<functional>"
  - "std.<functional>"
  - "std::<functional>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函子"
  - "functional 标头"
ms.assetid: 7dd463e8-a29f-49bc-aedd-8fa53b54bfbc
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; 功能 &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义标准库函数，用于帮助构造 *函数对象*-也称为函子-及其绑定程序。 函数对象是用于定义 `operator()` 的类型的对象。 函数对象可以是函数指针，但该对象更常用于存储可在函数调用过程中访问的其他信息。  
  
## <a name="syntax"></a>语法  
  
```  
#include <functional>  
```  
  
## <a name="remarks"></a>备注  
 算法要求提供两种类型的函数对象：一元对象和二元对象。 一元函数对象需要一个参数，二元函数对象需要两个参数。 函数对象和函数指针均可以作为算法的谓词传递，但函数对象还能自适应，并增加 STL 的作用域、灵活性和效率。 例如，如果需要在将值传递给算法之前将其绑定到函数，则不能使用函数指针。 函数适配器将函数指针转换为可以绑定到值的自适应函数对象。 标头 \< 功能> 还包含允许成员函数作为自适应函数对象调用的成员函数适配器。 如果函数具有指定其自变量和返回类型的嵌套类型声明，则它是自适应的。 C++ 标准要求从 unary_function 或 binary_function 基类继承所有标准对象类，以实现此适应性。 函数对象及其适配器允许 STL 升级现有应用程序，并帮助将 STL 集成到 C++ 编程环境。  
  
  [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 实现中的函数对象 \< 功能> 包括 *透明运算符函子*, ，这是标准的专用化函数对象和不带任何模板参数，并执行能够完美转接函数自变量并完美返回结果。 此功能是 C++14 标准草案规范的一部分。 这些模板专用化不要求在调用算术、比较、逻辑和按位运算符函子时指定参数类型。 可为你自己的类型或类型的异类组合重载算术、比较、逻辑或按位运算符，然后将透明运算符函子用作函数自变量。 例如，如果你的类型 *MyType* 实现 `operator<`, ，可以调用 `sort(my_collection.begin(), my_collection.end(), less<>())` 而不是显式指定类型 `sort(my_collection.begin(), my_collection.end(), less<MyType>())`。  
  
## <a name="c11c14-implementation"></a>C++11/C++14 实现  
 C++11/C++14 的 Visual C++ 实现中添加了以下功能：  
  
-   A *调用签名* 是跟一个用圆括号括起来以逗号分隔列表的零个或多个自变量类型的返回类型的名称。  
  
-   A *可调用类型* 是指向函数、 指向成员函数的指针、 指向成员数据的指针或其对象可以立即显示函数调用运算符左侧的类类型的指针。  
  
-   A *可调用对象* 是可调用类型的对象。  
  
-   A *调用包装器类型* 是保持可调用对象，并支持转发到该对象调用操作的类型。  
  
-   A *调用包装器* 是调用包装器类型的对象。  
  
-   A *目标对象* 是由调用包装器对象持有的可调用对象。  
  
 伪函数 `INVOKE(f, t1, t2, ..., tN)` 表示以下内容之一：  
  
- 当 `f` 是指向类 `T` 的成员函数的指针，且 `t1` 是类型 `T` 的对象、对类型 `T` 的对象的引用或对派生自 `T` 的类型的对象的引用时，它表示 `(t1.*f)(t2, ..., tN)`。  
  
- 当 `f` 是指向类 `T` 的成员函数的指针，且 `t1` 不是上一项中描述的任一类型时，它表示 `((*t1).*f)(t2, ..., tN)`。  
  
- 当 N == 1，且 `f` 是指向类 `T` 的成员数据的指针，`t1` 是类型 `T` 的对象、对类型 `T` 的对象的引用或对派生自 `T` 的类型的对象的引用时，它表示 `t1.*f`。  
  
- 当 N == 1，且 `f` 是指向类 `T` 的成员数据的指针，`t1` 不是上一项中描述的任一类型时，它表示 `(*t1).*f`。  
  
- 在所有其他情况下，它表示 `f(t1, t2, ..., tN)`。  
  
 伪函数 `INVOKE(f, t1, t2, ..., tN, R)` 表示将 `INVOKE(f, t1, t2, ..., tN)` 隐式转换为 `R`。  
  
 如果调用包装器具有 *弱结果类型*, ，其成员类型的类型 `result_type` 根据类型 `T` 目标对象的包装，如下所示︰  
  
-   如果 `T` 是指向函数的指针，则 `result_type` 是 `T` 的返回类型的同义词。  
  
-   如果 `T` 是指向成员函数的指针，则 `result_type` 是 `T` 的返回类型的同义词。  
  
-   如果 `T` 是具有成员类型 `result_type` 的类类型，则 `result_type` 是 `T::result_type` 的同义词。  
  
-   否则不存在成员 `result_type`。  
  
 每个调用包装器具有一个移动构造函数和一个复制构造函数。 A *简单调用包装器* 是具有的赋值运算符和其复制构造函数、 移动构造函数和赋值运算符不会引发异常的调用包装器。 A *转发调用包装器* 是可以使用任意自变量列表调用的调用包装器，并传递给已包装可调用对象作为引用参数。 所有右值自变量都以右值引用的方式传递，所有左值自变量都以左值引用的方式传递。  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[bad_function_call](../standard-library/bad-function-call-class.md)|一个类来描述引发的异常以指示调用 `operator()` 上 [函数](../standard-library/function-class.md) 对象失败，因为该对象为空。|  
|[binary_negate](../standard-library/binary-negate-class.md)|一种模板类，用于提供成员函数，对指定二元函数的返回值进行求反。|  
|[binder1st](../standard-library/binder1st-class.md)|一种模板类，用于提供构造函数，通过将二元函数的第一个自变量绑定到指定的值，将二元函数对象转换为一元函数对象。|  
|[binder2nd](../standard-library/binder2nd-class.md)|一种模板类，用于提供构造函数，通过将二元函数的第二个自变量绑定到指定的值，将二元函数对象转换为一元函数对象。|  
|[const_mem_fun_ref_t](../standard-library/const-mem-fun-ref-t-class.md)|一种适配器类，在使用引用自变量进行初始化的情况下，该类允许将不带任何自变量的 const 成员函数作为一元函数对象调用。|  
|[const_mem_fun_t](../standard-library/const-mem-fun-t-class.md)|一种适配器类，在使用指针自变量进行初始化的情况下，该类允许将不带任何自变量的 const 成员函数作为一元函数对象调用。|  
|[const_mem_fun1_ref_t](../standard-library/const-mem-fun1-ref-t-class.md)|一种适配器类，在使用引用自变量进行初始化的情况下，该类允许将仅带一个自变量的 const 成员函数作为二元函数对象调用。|  
|[const_mem_fun1_t](../standard-library/const-mem-fun1-t-class.md)|一种适配器类，在使用指针自变量进行初始化的情况下，该类允许将仅带一个自变量的 const 成员函数作为二元函数对象调用。|  
|[函数](../standard-library/function-class.md)|一种类，用于包装可调用的对象。|  
|[哈希](../standard-library/hash-class.md)|一种类，用于计算值的哈希代码。|  
|[is_bind_expression](../standard-library/is-bind-expression-class.md)|一种类，用于调用 `bind` 时是否会生成特定的类型。|  
|[is_placeholder](../standard-library/is-placeholder-class.md)|一种类，用于测试特定类型是否为占位符。|  
|[mem_fun_ref_t](../standard-library/mem-fun-ref-t-class.md)|一种适配器类，它允许 **non_const** 不采用任何参数作为一元函数对象在使用引用参数进行初始化时调用的成员函数。|  
|[mem_fun_t](../standard-library/mem-fun-t-class.md)|一种适配器类，它允许 **non_const** 不采用任何参数作为一元函数对象在使用指针参数进行初始化时调用的成员函数。|  
|[mem_fun1_ref_t](../standard-library/mem-fun1-ref-t-class.md)|一种适配器类，它允许 **non_const** 采用单个参数作为二元函数对象在使用引用参数进行初始化时调用的成员函数。|  
|[mem_fun1_t](../standard-library/mem-fun1-t-class.md)|一种适配器类，它允许 **non_const** 采用单个参数作为二元函数对象在使用指针参数进行初始化时调用的成员函数。|  
|[pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md)|将二元函数指针转换为自适应二元函数。|  
|[pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md)|将一元函数指针转换为自适应一元函数。|  
|[reference_wrapper](../standard-library/reference-wrapper-class.md)|一种类，用于包装引用。|  
|[result_of](../standard-library/result-of-class2.md)|一种结构，用于保存已包装可调用对象的返回类型。|  
|[unary_negate](../standard-library/unary-negate-class.md)|一种模板类，用于提供成员函数，对指定一元函数的返回值进行求反。|  
  
### <a name="functions"></a>函数  
  
|||  
|-|-|  
|[绑定](../Topic/%3Cfunctional%3E%20functions.md#bind_function)|将自变量绑定到可调用对象。|  
|[bind1st](../Topic/%3Cfunctional%3E%20functions.md#bind1st_function)|一种帮助程序模板类，用于创建适配器，通过将二元函数的第一个自变量绑定到指定的值，将二元函数对象转换为一元函数对象。|  
|[bind2nd](../Topic/%3Cfunctional%3E%20functions.md#bind2nd_function)|一种帮助程序模板类，用于创建适配器，通过将二元函数的第二个自变量绑定到指定的值，将二元函数对象转换为一元函数对象。|  
|[bit_and](../Topic/%3Cfunctional%3E%20functions.md#bit_and_function)|返回两个参数的按位逻辑 AND（二元运算符 &）。|  
|[bit_not](../Topic/%3Cfunctional%3E%20functions.md#bit_not_function)|返回两个参数的按位逻辑求反（二元运算符 ~）。|  
|[bit_or](../Topic/%3Cfunctional%3E%20functions.md#bit_or_function)|返回的按位逻辑 OR (运算符 &#124;) 的两个参数。|  
|[bit_xor](../Topic/%3Cfunctional%3E%20functions.md#bit_xor_function)|返回两个参数的按位逻辑 XOR（二元运算符 ^）。|  
|[cref](../Topic/%3Cfunctional%3E%20functions.md#cref_function)|从变量构造常量 `reference_wrapper`。|  
|[mem_fn](../Topic/%3Cfunctional%3E%20functions.md#mem_fn_function)|生成一个简单的调用包装器。|  
|[mem_fun](../Topic/%3Cfunctional%3E%20functions.md#mem_fun_function)|帮助程序模板函数，在使用指针自变量进行初始化的情况下，用来构造成员函数的函数对象适配器。|  
|[mem_fun_ref](../Topic/%3Cfunctional%3E%20functions.md#mem_fun_ref_function)|帮助程序模板函数，在使用引用自变量进行初始化的情况下，用来构造成员函数的函数对象适配器。|  
|[not1](../Topic/%3Cfunctional%3E%20functions.md#not1_function)|返回一元谓词的补集。|  
|[not2](../Topic/%3Cfunctional%3E%20functions.md#not2_function)|返回二元谓词的补集。|  
|[ptr_fun](../Topic/%3Cfunctional%3E%20functions.md#ptr_fun_function)|帮助程序模板函数，用于将一元和二元函数指针分别转换为一元和二元自适应函数。|  
|[ref](../Topic/%3Cfunctional%3E%20functions.md#ref_function)|从变量构造常量 `reference_wrapper`。|  
|[交换](../Topic/%3Cfunctional%3E%20functions.md#swap_function)|交换两个 `function` 对象。|  
  
### <a name="structs"></a>结构  
  
|||  
|-|-|  
|[binary_function](../standard-library/binary-function-struct.md)|空基类，定义可能由提供二元函数对象的派生类继承的类型。|  
|[会将其划分](../standard-library/divides-struct.md)|此类提供预定义的函数对象，后者对指定值类型的元素执行除法算术运算。|  
|[equal_to](../standard-library/equal-to-struct.md)|此二元谓词测试指定类型的一个值是否等于该类型的另一个值。|  
|[更高版本](../standard-library/greater-struct.md)|此二元谓词测试指定类型的一个值是否大于该类型的另一个值。|  
|[greater_equal](../standard-library/greater-equal-struct.md)|此二元谓词测试指定类型的一个值是否大于或等于该类型的另一个值。|  
|[小于](../standard-library/less-struct.md)|此二元谓词测试指定类型的一个值是否小于该类型的另一个值。|  
|[less_equal](../standard-library/less-equal-struct.md)|此二元谓词测试指定类型的一个值是否小于或等于该类型的另一个值。|  
|[logical_and](../standard-library/logical-and-struct.md)|此类提供预定义的函数对象，后者对指定值类型的元素执行合取逻辑运算，并测试结果是 ture 还是 false。|  
|[logical_not](../standard-library/logical-not-struct.md)|此类提供预定义的函数对象，后者对指定值类型的元素执行求反逻辑运算，并测试结果是 ture 还是 false。|  
|[logical_or](../standard-library/logical-or-struct.md)|此类提供预定义的函数对象，后者对指定值类型的元素执行析取逻辑运算，并测试结果是 ture 还是 false。|  
|[减号](../standard-library/minus-struct.md)|此类提供预定义的函数对象，后者对指定值类型的元素执行减法算术运算。|  
|[取模](../standard-library/modulus-struct.md)|此类提供预定义的函数对象，后者对指定值类型的元素执行取模算术运算。|  
|[乘以](../standard-library/multiplies-struct.md)|此类提供预定义的函数对象，后者对指定值类型的元素执行乘法算术运算。|  
|[要求反](../standard-library/negate-struct.md)|此类提供预定义的函数对象，后者返回元素值的负值。|  
|[not_equal_to](../standard-library/not-equal-to-struct.md)|此二元谓词测试指定类型的一个值是否不等于该类型的另一个值。|  
|[加号](../standard-library/plus-struct.md)|此类提供预定义的函数对象，后对指定值类型的元素执行加法算术运算。|  
|[unary_function](../standard-library/unary-function-struct.md)|空基类，定义可能由提供一元函数对象的派生类继承的类型。|  
  
### <a name="objects"></a>对象  
  
|||  
|-|-|  
|[_1.._M](../standard-library/1-object.md)|可替换自变量的占位符。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 = =](../Topic/%3Cfunctional%3E%20operators.md#operator_eq_eq)|不允许对可调用对象进行相等性比较。|  
|[运算符 ！ =](../Topic/%3Cfunctional%3E%20operators.md#operator_neq)|不允许对可调用对象进行不等性比较。|  
  
## <a name="see-also"></a>请参阅  
 [标头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)

