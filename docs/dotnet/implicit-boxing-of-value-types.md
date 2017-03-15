---
title: "值类型的隐式装箱 | Microsoft Docs"
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
helpviewer_keywords: 
  - "__box 关键字"
  - "装箱"
  - "装箱, __box 关键字"
  - "装箱, Visual C++"
  - "值类型, 装箱"
ms.assetid: 9597c92f-a3fe-44af-ad80-f9d656847a35
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 值类型的隐式装箱
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，值类型的装箱已发生更改。  
  
 在语言设计中，我们在本该强调该功能的实际经验的地方强加了某种哲学观点，在实践中，这是一个错误。  打个比方，在最初的多继承语言设计中，Stroustrup 决定未能在派生类构造函数中初始化虚拟基类子对象，因此该语言要求任何充当虚拟基类的类都必须定义一个默认构造函数。  任何后续的虚拟派生都将调用该默认构造函数。  
  
 虚拟基类层次结构的问题是共享虚拟子对象的初始化的职责对于每个后续派生都不同。  例如，如果定义其初始化要求分配缓冲区的基类，该缓冲区的用户指定的大小可能会作为参数传递到构造函数。  之后，如果提供两个后续的虚拟派生，将它们命名为 `inputb` 和 `outputb`，使它们分别向基类构造函数提供一个特定的值。  现在，当我同时从 `inputb` 和 `outputb` 派生一个 `in_out` 类时，在逻辑上，计算共享虚拟基类子对象的这两个值将是不可能的。  
  
 因此，在最初的语言设计中，Stroustrup 不允许在派生类构造函数的成员初始化列表内进行虚拟基类的显式初始化。  虽然这种处理方式解决了问题，但实践中证明无法指示虚拟基类的初始化是不可行的。  国家医疗卫生研究院的 Keith Gorlen，也就是实现了 SmallTalk 集合库的免费软件版本（称为 nihcl）的研究人员，为说服 Stroustrup 必须推出更为灵活的语言设计立下了汗马功劳。  
  
 面向对象的层次结构设计的一个原则是，派生类应只负责它的直接基类的非私有实现。  为了支持较为灵活的虚拟继承初始化设计，Stroustrup 不得不突破该原则。  层次结构中的派生程度最高的类负责进行所有虚拟子对象初始化，无论这种初始化发生在层次结构中的哪一级。  例如，`inputb` 和 `outputb` 都负责显式初始化它们的直接虚拟基类。  当 `in_out` 同时从 `inputb` 和 `outputb` 派生时，`in_out` 将负责初始化曾被移除的虚拟基类，而在 `inputb` 和 `outputb` 内进行的显式初始化则被取消。  
  
 这提供了语言开发人员所需要的灵活性，缺点是语义太复杂。  如果将虚拟基类限制为无状态，并直接允许它指定接口，语义复杂的问题也会得到解决。  在 C\+\+ 内这是一个推荐的设计思路。  在 CLR 编程中，它的地位被提升到与接口类型同等的策略高度。  
  
 这里是一个简单的代码示例，在该示例中，不必进行显式装箱：  
  
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
  
 正如您所看到的，进行了许多装箱操作。  在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 下，值类型装箱是隐式的：  
  
```  
// new syntax makes boxing implicit  
array<int>^ my1DIntArray = {1,2,3,4,5};  
array<Object^>^ myObjArray = {26,27,28,29,30};  
  
Console::WriteLine( "{0}\t{1}\t{2}", 0,   
   my1DIntArray->GetLowerBound( 0 ),   
   my1DIntArray->GetUpperBound( 0 ) );  
```  
  
## 请参阅  
 [值类型及其行为 \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [装箱](../windows/boxing-cpp-component-extensions.md)