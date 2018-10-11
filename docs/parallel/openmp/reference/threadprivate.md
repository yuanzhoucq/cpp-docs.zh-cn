---
title: threadprivate |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- threadprivate
dev_langs:
- C++
helpviewer_keywords:
- threadprivate OpenMP directive
ms.assetid: 3515aaed-6f9d-4d59-85eb-342378bea2d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b769b5aa5f46b9a4b815424a0c4178cf4504ab5
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082431"
---
# <a name="threadprivate"></a>threadprivate

指定一个变量是线程私有的。

## <a name="syntax"></a>语法

```
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>参数

*var*<br/>
你想要对线程进行私有变量的以逗号分隔列表。 `var` 必须是全局或命名空间的范围内的变量或静态局部变量。

## <a name="remarks"></a>备注

`threadprivate`指令支持任何 OpenMP 子句。

有关详细信息，请参阅[2.7.1 threadprivate 指令](../../../parallel/openmp/2-7-1-threadprivate-directive.md)。

`threadprivate`指令基于[线程](../../../cpp/thread.md)`__declspec`特性; 限制 **__declspec （thread)** 适用于`threadprivate`。

不能使用`threadprivate`中将通过加载任意 DLL [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya)。  这包括与加载的 Dll [/DELAYLOAD （延迟加载导入）](../../../build/reference/delayload-delay-load-import.md)，该列也会使用**LoadLibrary**。

可以使用`threadprivate`以静态方式在进程启动时加载的 DLL 中。

因为`threadprivate`基于 **__declspec （thread)**、`threadprivate`变量将在任何线程已启动的过程中，而不仅仅是这些线程属于按并行区域生成一个线程团队中存在。  这是要注意的因为您可能会注意到，例如，构造函数的实现细节`threadprivate`通常则预期更多调用用户定义类型。

一个`threadprivate`destructable 类型的变量不能保证具有调用其析构函数。  例如：

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

用户具有关于构成并行区域的线程将终止时无法控制。  如果这些线程存在时在进程退出，线程将不会通知有关进程退出，并且析构函数不会为调用`threaded_var`除退出任何线程上 （此处，主线程）。  使代码不应统计上的正确析构`threadprivate`变量。

## <a name="example"></a>示例

有关使用的示例`threadprivate`，请参阅[专用](../../../parallel/openmp/reference/private-openmp.md)。

## <a name="see-also"></a>请参阅

[指令](../../../parallel/openmp/reference/openmp-directives.md)