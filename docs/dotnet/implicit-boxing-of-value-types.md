---
title: 值类型的隐式装箱 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxing, Visual C++
- __box keyword
- boxing
- boxing, __box keyword
- value types, boxed
ms.assetid: 9597c92f-a3fe-44af-ad80-f9d656847a35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e9c232dba6d766d0855bb4bb29e33d85b5fd5a2d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387583"
---
# <a name="implicit-boxing-of-value-types"></a>值类型的隐式装箱

值类型的装箱已从托管扩展中的 c + + 更改为 Visual c + +。

在语言设计中，我们在强加哲学观点强调了功能的实际经验，并在实践中，它是一个错误。 打个比方，在原始多个继承语言设计中，Stroustrup 决定在派生的类构造函数的内部，无法初始化虚拟基类的子对象，并因此语言所需的任何充当虚拟基的类类必须定义一个默认构造函数。 它是该默认构造函数所调用的任何后续虚拟派生的。

虚拟基类层次结构的问题是共享的虚拟子对象的初始化的责任转移与每个后续派生。 例如，如果我定义基类的类初始化需要分配的缓冲区中，用户指定的缓冲区的大小可能会作为参数传递给构造函数。 如果我再提供两个后续虚拟派生，称之为`inputb`和`outputb`，每个都提供对基类构造函数的特定值。 现在，当我派生`in_out`从这两个类`inputb`和`outputb`，既不共享的虚拟基类的子对象到这些值有意义地有权评估。

因此，在原始语言设计中，Stroustrup 不允许显式初始化虚拟基类的成员初始化列表中的派生的类构造函数。 这解决了问题，而在实践中不能直接虚拟基类的初始化被证明不可行。 Keith Gorlen 国家/地区 Institute 的运行状况，用户必须实现名为 nihcl SmallTalk 集合库的免费软件版本，已在说服他不得不拿出更灵活的语言设计的 Stroustrup 的原则语音。

面向对象的层次结构设计原则，派生的类应考虑如何仅其即时基类，这些类的非私有实现。 为了支持虚拟继承灵活初始化设计，Stroustrup 必须违反此原则。 层次结构中派生程度最高的类不承担责任而不考虑如何深入到层次结构中发生的所有虚拟子对象初始化。 例如，`inputb`和`outputb`都负责显式初始化其即时虚拟基类。 当`in_out`从这两个派生`inputb`并`outputb`，`in_out`将负责一次初始化中删除虚拟基类，并且初始化中显式`inputb`和`outputb`是禁止显示。

这提供了所需的语言的开发人员，但代价是会复杂语义的灵活性。 如果我们限制虚拟基类作为无状态，只需让该代码以指定一个接口，将得到解决复杂的这种负担。 这是 c + + 中推荐的设计思路。 在 CLR 编程，它被引发到具有接口类型的策略。

下面是简单的代码示例-并在这种情况下，显式装箱是不必要：

```
// Managed Extensions for C++ requires explicit __box operation
int my1DIntArray __gc[] = { 1, 2, 3, 4, 5 };
Object* myObjArray __gc[] = {
   __box(26), __box(27), __box(28), __box(29), __box(30)
};

Console::WriteLine( "{0}\t{1}\t{2}", __box(0),
   __box(my1DIntArray->GetLowerBound(0)),
   __box(my1DIntArray->GetUpperBound(0)) );
```

正如您所看到的没有很多装箱操作。 在 Visual c + +，值类型装箱是隐式：

```
// new syntax makes boxing implicit
array<int>^ my1DIntArray = {1,2,3,4,5};
array<Object^>^ myObjArray = {26,27,28,29,30};

Console::WriteLine( "{0}\t{1}\t{2}", 0,
   my1DIntArray->GetLowerBound( 0 ),
   my1DIntArray->GetUpperBound( 0 ) );
```

## <a name="see-also"></a>请参阅

[值类型及其行为 (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[装箱](../windows/boxing-cpp-component-extensions.md)