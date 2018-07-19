---
title: 值类型的隐式装箱 |Microsoft 文档
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
ms.openlocfilehash: f1f5a455333e5cb40b63d5a5237b2df053cef194
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132214"
---
# <a name="implicit-boxing-of-value-types"></a>值类型的隐式装箱
值类型装箱已从托管扩展中的 c + + 更改为 Visual c + +。  
  
 在语言设计中，我们在强加理论观点强调实际经验的功能，并在实践中，这是一个错误。 打个比方，在原始多个继承语言设计，Stroustrup 决定派生的类构造函数的内部，无法初始化虚拟基类的子对象，因此该语言要求，充当虚拟基的任何类类必须定义一个默认构造函数。 它是该默认构造函数将调用的任何后续虚拟派生。  
  
 虚拟基类层次结构的问题是负责共享的虚拟子对象的初始化会随每个后续派生之切换。 例如，如果定义的基类的类初始化需要分配的缓冲区，该缓冲区的用户指定大小可能会传递作为自变量的构造函数。 如果我然后提供两个后续虚拟派生，则调用它们`inputb`和`outputb`，每一个都提供对基类构造函数的特定值。 现在，当我派生`in_out`从这两个类`inputb`和`outputb`，这些值与共享虚拟基类的子对象都不可以切合实际地允许评估。  
  
 因此，在原始语言设计中，Stroustrup 不允许显式初始化虚拟基类的成员初始化列表中的派生的类构造函数。 这解决了这个问题，而在实践中无法直接虚拟基类的初始化的确不可行。 Keith Gorlen 国家/地区研究院的运行状况，用户必须实现调用 nihcl SmallTalk 集合库的免费版本，已在诱使他必须附带更灵活的语言设计的 Stroustrup 原则语音。  
  
 面向对象的层次结构设计的原则，派生的类应负责本身只能使用其即时基类，这些类的非私有实现。 为了支持虚拟继承灵活初始化设计，Stroustrup 必须违反这一原则。 层次结构中的大多数派生的类负责而不考虑如何深入到层次结构中发生的所有虚拟子对象初始化。 例如，`inputb`和`outputb`都负责显式初始化其即时虚拟基类。 当`in_out`从这两个派生`inputb`和`outputb`，`in_out`将负责初始化一次删除虚拟基类，并且初始化内进行的显式`inputb`和`outputb`是禁止显示。  
  
 这提供所需的语言的开发人员，但同时会增加复杂的语义的灵活性。 如果我们限制虚拟基类作为无状态，只需让它以指定一个接口，将得到解决这种负担的复杂性。 这是 c + + 中推荐的设计思路。 在 CLR 编程，它将引发到策略所具有的接口类型。  
  
 此处是一个简单的代码示例并在这种情况下，显式装箱是不必要的：  
  
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
  
 如你所见，有很多整个装箱操作。 在 Visual c + +，值类型装箱是隐式：  
  
```  
// new syntax makes boxing implicit  
array<int>^ my1DIntArray = {1,2,3,4,5};  
array<Object^>^ myObjArray = {26,27,28,29,30};  
  
Console::WriteLine( "{0}\t{1}\t{2}", 0,   
   my1DIntArray->GetLowerBound( 0 ),   
   my1DIntArray->GetUpperBound( 0 ) );  
```  
  
## <a name="see-also"></a>请参阅  
 [值类型和它们的行为 (C + + /cli CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [装箱](../windows/boxing-cpp-component-extensions.md)