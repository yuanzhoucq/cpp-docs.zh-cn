---
title: "使用 Lambda、 函数对象和受限的函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afec84ba6e3c007e576c37b4a7afc71fe62691ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-lambdas-function-objects-and-restricted-functions"></a>使用 Lambda 表达式、函数对象和受限函数
作为自变量对的调用中指定你想要在快捷键上运行的 c + + AMP 代码[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。 你可以提供 lambda 表达式或函数对象 （函子），作为该参数。 此外，lambda 表达式或函数对象可以调用 c + + AMP 限制的函数。 本主题使用数组添加算法来演示 lambda、 函数对象和受限的函数。 下面的示例演示不使用 c + + AMP 代码的算法。 创建两个一维数组的长度相等。 相应的整数元素添加，并存储在第三个一维数组。 不使用 c + + AMP。  
  
```cpp  
void CpuMethod() {  
 
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
 
    for (int idx = 0; idx <5; idx++)  
 {  
    sumCPP[idx] = aCPP[idx] + bCPP[idx];  
 }  
 
    for (int idx = 0; idx <5; idx++)  
 {  
    std::cout <<sumCPP[idx] <<"\n";  
 }  
}  
 
```  
  
## <a name="lambda-expression"></a>Lambda 表达式  
 使用 lambda 表达式是使用 c + + AMP 来重写代码的最直接方式。  
  
```cpp  
void AddArraysWithLambda() {  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
 
    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

 
    parallel_for_each(
 sum.extent, 
 [=](index<1> idx) restrict(amp)  
 {  
    sum[idx] = a[idx] + b[idx];  
 });

 
    for (int i = 0; i <5; i++) {  
    std::cout <<sum[i] <<"\n";  
 }  
}  
 
```  
  
 Lambda 表达式必须包括一个索引的参数，并且必须包括`restrict(amp)`。 在示例中， [array_view](../../parallel/amp/reference/array-view-class.md) `sum`对象具有秩为 1。 因此，lambda 语句的参数是[索引](../../parallel/amp/reference/index-class.md)具有秩为 1 的对象。 在运行时，lambda 表达式是一次每个元素执行中[array_view](../../parallel/amp/reference/array-view-class.md)对象。 有关详细信息，请参阅[Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)。  
  
## <a name="function-object"></a>Function 对象  
 你可以将快捷键代码纳入函数对象。  
  
```cpp  
class AdditionFunctionObject  
{  
public:  
    AdditionFunctionObject(const array_view<int, 1>& a,  
    const array_view<int, 1>& b,  
    const array_view<int, 1>& sum)  
 : a(a), b(b), sum(sum)  
 {  
 }  
 
    void operator()(index<1> idx) restrict(amp)  
 {  
    sum[idx] = a[idx] + b[idx];  
 }  
 
private:  
    array_view<int, 1> a;  
    array_view<int, 1> b;  
    array_view<int, 1> sum;  
};  
 
void AddArraysWithFunctionObject() {  
 
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
 
    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

 
    parallel_for_each(
 sum.extent, 
    AdditionFunctionObject(a, b, sum));

 
    for (int i = 0; i <5; i++) {  
    std::cout <<sum[i] <<"\n";  
 }  
}  
 
```  

 函数对象必须包含一个构造函数，并且必须包括函数调用运算符的重载。 函数调用运算符必须包含一个索引的参数。 作为第二个参数传递的函数对象实例[parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)方法。 在此示例中，三个[array_view](../../parallel/amp/reference/array-view-class.md)对象传递给函数对象构造函数。 [Array_view](../../parallel/amp/reference/array-view-class.md)对象`sum`一个秩为 1。 因此，函数调用运算符的参数是[索引](../../parallel/amp/reference/index-class.md)具有秩为 1 的对象。 在运行时，该函数执行一次的每个元素[array_view](../../parallel/amp/reference/array-view-class.md)对象。 有关详细信息，请参阅[函数调用](../../cpp/function-call-cpp.md)和[c + + 标准库中的函数对象](../../standard-library/function-objects-in-the-stl.md)。  
  
## <a name="c-amp-restricted-function"></a>C + + AMP 限制函数  
 可以通过创建受限制的功能，并从 lambda 表达式或函数对象调用它，进一步挑选快捷键代码。 下面的代码示例演示如何从 lambda 表达式中调用受限制的功能。  
  
```cpp  
void AddElementsWithRestrictedFunction(index<1> idx, array_view<int, 1> sum, array_view<int, 1> a, array_view<int, 1> b) restrict(amp)  
{  
    sum[idx] = a[idx] + b[idx];  
}  
 
void AddArraysWithFunction() {  
 
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
 
    array_view<int, 1> a(5, aCPP);

    array_view<int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

 
    parallel_for_each(
 sum.extent, 
 [=](index<1> idx) restrict(amp)  
 {  
    AddElementsWithRestrictedFunction(idx, sum, a, b);

 });

 
    for (int i = 0; i <5; i++) {  
    std::cout <<sum[i] <<"\n";  
 }  
}  
 
```  
  
 受限制的功能必须包括`restrict(amp)`符合中所述的限制和[限制 (c + + AMP)](../../cpp/restrict-cpp-amp.md)。  
  
## <a name="see-also"></a>请参阅  
 [C + + AMP (c + + Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)   
 [函数调用](../../cpp/function-call-cpp.md)   
 [C + + 标准库中的函数对象](../../standard-library/function-objects-in-the-stl.md)   
 [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

