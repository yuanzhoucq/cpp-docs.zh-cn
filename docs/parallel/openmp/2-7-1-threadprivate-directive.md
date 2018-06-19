---
title: 2.7.1 threadprivate 指令 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9912ccbfa6f5773ec1e523245f75e675bb82244
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692647"
---
# <a name="271-threadprivate-directive"></a>2.7.1 threadprivate 指令
`threadprivate`指令使命名的文件范围、 命名空间范围或静态的块范围变量中指定*变量列表*专用于一个线程。 *变量列表*是不具有不完整类型的变量的以逗号分隔列表。 语法`threadprivate`指令是，如下所示：  
  
```  
#pragma omp threadprivate(variable-list) new-line  
```  
  
 每个副本`threadprivate`变量一次，在初始化到该副本的第一个引用之前的计划中并按常规方式的未指定点 （即，为将在该程序的串行执行过程中初始化的主副本）。 请注意，如果在一个显式初始值设定项中引用对象`threadprivate`一份该变量，则首次引用之前修改变量和对象的值，则行为是未指定。  
  
 如与任何私有变量，线程不能引用另一个线程份`threadprivate`对象。 在串行区域和程序的主区域中，引用将发送到主线程的对象的副本。  
  
 在执行第一个并行区域中的数据后`threadprivate`对象保证以保留仅已禁用，如果动态线程机制和线程数保持为所有并行区域不变。  
  
 对限制`threadprivate`指令如下所示：  
  
-   A`threadprivate`文件范围或命名空间范围变量的指令必须显示在外部的任何定义或声明，以及必须词法前面的所有引用的任何变量在其列表中。  
  
-   在每个变量*变量列表*的`threadprivate`在文件或命名空间范围内的指令必须引用在词法上之前指令的文件或命名空间范围内的变量声明。  
  
-   A`threadprivate`指令为静态的块范围变量必须显示在变量的作用域中，不能在嵌套的范围。 词法上指令必须在所有引用的任何变量都前在其列表中。  
  
-   在每个变量*变量列表*的`threadprivate`块范围中的指令必须引用相同的词法之前指令的范围中的变量声明。 变量的声明必须使用静态存储类说明符。  
  
-   如果在指定变量`threadprivate`指令中一个翻译单元，它必须按指定`threadprivate`指令在其中声明每个翻译单元中。  
  
-   A`threadprivate`变量不能出现在除任何子句中`copyin`， `copyprivate`， `schedule`， `num_threads`，或**如果**子句。  
  
-   地址`threadprivate`变量不是地址常量。  
  
-   A`threadprivate`变量必须没有不完整类型或引用类型。  
  
-   A`threadprivate`与非 POD 类类型的变量必须具有可访问的明确的复制构造函数，如果它用一个显式初始值设定项声明。  
  
 下面的示例演示如何修改变量时，将显示在初始值设定项可能会导致未指定的行为，以及如何通过使用一个辅助对象和复制构造函数来避免此问题。  
  
```  
int x = 1;  
T a(x);  
const T b_aux(x); /* Capture value of x = 1 */  
T b(b_aux);  
#pragma omp threadprivate(a, b)  
  
void f(int n) {  
   x++;  
   #pragma omp parallel for  
   /* In each thread:  
   * Object a is constructed from x (with value 1 or 2?)  
   * Object b is copy-constructed from b_aux  
   */  
   for (int i=0; i<n; i++) {  
      g(a, b); /* Value of a is unspecified. */  
   }  
}  
```  
  
## <a name="cross-references"></a>交叉引用：  
  
-   动态线程，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)页 39 上。  
  
-   `OMP_DYNAMIC` 环境变量，请参阅[部分 4.3](../../parallel/openmp/4-3-omp-dynamic.md)页 49 上。