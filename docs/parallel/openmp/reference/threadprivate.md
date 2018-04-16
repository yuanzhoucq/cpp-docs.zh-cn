---
title: "threadprivate |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- threadprivate
dev_langs:
- C++
helpviewer_keywords:
- threadprivate OpenMP directive
ms.assetid: 3515aaed-6f9d-4d59-85eb-342378bea2d3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 55a50d2387662fe42c04d61a8e98153aad95c835
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="threadprivate"></a>threadprivate
指定的变量是私有的线程。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma omp threadprivate(var)  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `var`  
 你想要为某个线程设为专用的变量的以逗号分隔列表。 `var` 必须是全局或命名空间的范围变量或静态局部变量。  
  
## <a name="remarks"></a>备注  
 `threadprivate`指令支持没有 OpenMP 子句。  
  
 有关详细信息，请参阅[2.7.1 threadprivate 指令](../../../parallel/openmp/2-7-1-threadprivate-directive.md)。  
  
 `threadprivate`指令基于[线程](../../../cpp/thread.md)`__declspec`特性; 限制**__declspec （thread)**适用于`threadprivate`。  
  
 不能使用`threadprivate`中将通过加载的任何 DLL [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175)。  这包括与加载的 Dll [/DELAYLOAD （延迟加载导入）](../../../build/reference/delayload-delay-load-import.md)，该列也会使用**LoadLibrary**。  
  
 你可以使用`threadprivate`进程启动时以静态方式加载的 DLL 中。  
  
 因为`threadprivate`基于**__declspec （thread)**、`threadprivate`变量中启动在过程中，而不仅仅是这些线程属于线程团队由并行区域生成的任何线程不会存在。  这是你可能想要注意的因为你可能注意到，例如，构造函数的实现细节`threadprivate`调用通常则期的望多个用户定义类型。  
  
 A `threadprivate` destructable 类型的变量不能保证具有调用其析构函数。  例如:  
  
```  
struct MyType   
{  
    ~MyType();  
};  
  
MyType threaded_var;  
#pragma omp threadprivate(threaded_var)  
int main()   
{  
    #pragma omp parallel  
    {}  
}  
```  
  
 用户不具有控制并构成并行区域的线程将终止时。  如果这些线程存在在进程退出时，线程将不会通知有关进程退出，并且析构函数不会为调用`threaded_var`退出的一个以外的任何线程上 （此处，主线程）。  使代码不应依靠的正确析构`threadprivate`变量。  
  
## <a name="example"></a>示例  
 有关的使用示例`threadprivate`，请参阅[私有](../../../parallel/openmp/reference/private-openmp.md)。  
  
## <a name="see-also"></a>请参阅  
 [指令](../../../parallel/openmp/reference/openmp-directives.md)