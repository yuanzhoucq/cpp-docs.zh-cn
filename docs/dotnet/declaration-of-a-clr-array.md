---
title: CLR 数组的声明 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
ms.assetid: 36a8883c-2663-43f0-a90c-28f27035e036
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c3de17bb293e10c4e1a2287ef12b934633b1fe21
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426453"
---
# <a name="declaration-of-a-clr-array"></a>CLR 数组的声明

声明的语法，实例化和初始化托管的数组已从托管扩展 c + + 的 Visual c + +。

托管扩展中的 CLR 数组对象的声明是在其中标准数组声明的扩展`__gc`关键字被放置数组对象的名称和其可能是用逗号填充的维度，如下所示以下两个之间示例：

```
void PrintValues( Object* myArr __gc[]);
void PrintValues( int myArr __gc[,,]);
```

这已在新语法中，我们在其中使用类似于模板的声明类似于 c + + 标准库简化`vector`声明。 第一个参数指示的元素类型。 第二个参数指定的数组维度 （默认值为 1，因此只在多个维度都需要第二个参数）。 Array 对象本身是跟踪句柄，因此必须指定乘幂号的。 如果元素类型还是引用类型，它还需要乘幂号的。 例如，上面的示例中，当在新语法中，以表示如下所示：

```
void PrintValues( array<Object^>^ myArr );
void PrintValues( array<int,3>^ myArr );
```

由于引用类型是一个跟踪句柄，而不是对象，则可以指定为一个函数的返回类型的 CLR 数组。 （与此相反，它是不可能为函数的返回类型指定本机数组。）执行此操作在托管扩展语法是某种程度上不直观。 例如：

```
Int32 f() [];
int GetArray() __gc[];
```

在 Visual c + +，声明是要简单得多。 例如，应用于对象的

```
array<Int32>^ f();
array<int>^ GetArray();
```

这两个版本的语言支持的本地托管数组的速记初始化。 例如：

```
int GetArray() __gc[] {
   int a1 __gc[] = { 1, 2, 3, 4, 5 };
   Object* myObjArray __gc[] = {
      __box(26), __box(27), __box(28), __box(29), __box(30)
   };
   return a1;
}
```

大大简化了新语法中 (请注意，因为是在新语法中，隐式装箱`__box`运算符-请参阅[的值类型和及其行为 (C + + CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)有关的讨论):

```
array<int>^ GetArray() {
   array<int>^ a1 = {1,2,3,4,5};
   array<Object^>^ myObjArray = {26,27,28,29,30};
   return a1;
}
```

由于数组是 CLR 引用类型，每个数组对象的声明是跟踪句柄。 因此，必须在 CLR 堆上分配的数组对象。 （使用简写表示法隐藏托管的堆分配。）下面是在托管扩展中的数组对象初始化的显式窗体：

```
Object* myArray[] = new Object*[2];
String* myMat[,] = new String*[4,4];
```

在新语法中，`new`表达式已替换`gcnew`。 维度大小作为参数传递`gcnew`表达式，按如下所示：

```
array<Object^>^ myArray = gcnew array<Object^>(2);
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);
```

在新语法中，可以遵循显式初始化列表`gcnew`表达式，则这不支持在托管扩展中。 例如：

```
// explicit initialization list following gcnew
// was not supported in Managed Extensions
array<Object^>^ myArray =
   gcnew array<Object^>(4){ 1, 1, 2, 3 };
```

## <a name="see-also"></a>请参阅

[将托管类型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[数组](../windows/arrays-cpp-component-extensions.md)