---
title: 装箱 (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: 03304b902ced2c1e9776eeec90142380b984ee45
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230904"
---
# <a name="boxing-ccli"></a>装箱 (C++/CLI)

装箱是将值类型转换为类型 `object` 或值类型所实现的任何接口类型的过程。 当公共语言运行时（CLR）对值类型进行装箱时，它会在中包装值 `System.Object` 并将其存储在托管堆上。 取消装箱将从对象中提取值类型。 装箱是隐式的；取消装箱是显式的。

## <a name="related-articles"></a>相关文章

|Title|说明|
|-----------|-----------------|
|[如何：显式请求装箱](../dotnet/how-to-explicitly-request-boxing.md)|介绍如何在变量上显式请求装箱。|
|[如何：使用 gcnew 创建值类型和使用隐式装箱](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|演示如何使用 **`gcnew`** 来创建可放置在托管的垃圾回收堆上的装箱值类型。|
|[如何：取消装箱](../dotnet/how-to-unbox.md)|演示如何取消装箱和修改值。|
|[标准转换和隐式装箱](../dotnet/standard-conversions-and-implicit-boxing.md)|表明编译器在需要装箱的转换上选择了标准转换。|
|[用 c + +/CLI 进行 .NET 编程（Visual C++）](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Visual C++ 文档中有关 .NET 编程的顶级文章。|
