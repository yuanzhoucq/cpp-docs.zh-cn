---
title: "使用 Lambda 表达式、函数对象和受限函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 使用 Lambda 表达式、函数对象和受限函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

想在快捷键上要运行的 C\+\+ AMP 代码被指定为对 [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 方法调用中的一个参数。  您可以提供 Lambda 表达式或函数对象（伪函数）作为该参数。  此外，lambda 表达式或函数对象可以调用受限制的 C\+\+ AMP 函数。  本主题使用数组添加算法演示 lambda、函数对象和受限功能。  下面的示例显示了无 C\+\+ AMP 代码的算法。  创建了 2 个同等长度的一维数组。  对应整数元素添加并存储在第三个一维数组中。  不适用 C\+\+ AMP  
  
```cpp  
  
void CpuMethod() {  
  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        sumCPP[idx] = aCPP[idx] + bCPP[idx];  
    }  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        std::cout << sumCPP[idx] << "\n";  
    }  
}  
  
```  
  
## Lambda 表达式  
 使用 Lambda 表达式是使用 C\+\+ AMP 重新编写代码最直接的方式。  
  
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
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 Lambda 表达式必须包含一个索引参数和 `restrict(amp)`。  在示例中，[array\_view](../../parallel/amp/reference/array-view-class.md) `sum` 对象排在第 1 位。  因此，Lambda 语句的参数是一个具有级别 1 的[索引](../../parallel/amp/reference/index-class.md)对象。  运行时，Lambda 表达式为 [array\_view](../../parallel/amp/reference/array-view-class.md) 对象的每个元素执行一次。  有关详细信息，请参阅 [Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)。  
  
## Function 对象  
 您可以将快捷键代码分解成函数对象。  
  
```cpp  
  
class AdditionFunctionObject  
{  
public:  
    AdditionFunctionObject(const array_view<int, 1>& a,  
        const array_view<int, 1>& b,  
        const array_view<int, 1>& sum  
    )  
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
        AdditionFunctionObject(a, b, sum)  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 函数对象必须包含构造函数，并且必须包含函数调用运算符的重载。  函数调用运算符必须包含一个索引参数。  函数对象的实例将作为第二个参数传递到 [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 方法。  在此示例中，三个 [array\_view](../../parallel/amp/reference/array-view-class.md) 对象传递给函数对象构造函数。  [array\_view](../../parallel/amp/reference/array-view-class.md) 对象 `sum` 排在第 1。  因此，函数调用运算符的参数是一个具有级别 1 的[索引](../../parallel/amp/reference/index-class.md)对象。  运行时，此功能为 [array\_view](../../parallel/amp/reference/array-view-class.md) 对象的每个元素执行一次。  有关更多信息，请参见[函数调用 ](../../cpp/function-call-cpp.md)和[STL 中的函数对象](../../standard-library/function-objects-in-the-stl.md)。  
  
## C\+\+ AMP 受限功能  
 您可以通过创建受限函数和从 Lambda 表达式或函数对象进行调用来进一步分解快捷键代码。  下面的代码示例演示如何从 Lambda 表达式调用受限制的函数。  
  
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
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 受限函数必须包括 `restrict(amp)` 并符合 [restrict \(C\+\+ AMP\)](../../cpp/restrict-cpp-amp.md) 中所述的限制。  
  
## 请参阅  
 [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Lambda 表达式语法](../../cpp/lambda-expression-syntax.md)   
 [函数调用 ](../../cpp/function-call-cpp.md)   
 [STL 中的函数对象](../../standard-library/function-objects-in-the-stl.md)   
 [restrict \(C\+\+ AMP\)](../../cpp/restrict-cpp-amp.md)