---
title: "强制转换表示法和 safe_cast 引入&lt;&gt; |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- casting
- C-style casts and /clr, motivation for new cast notation
- safe_cast keyword [C++]
ms.assetid: 4eb1d000-3b93-4394-a37b-8b8563f8dc4d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 80d1a6e8b1a1691b4e76bfdc1232c95c22d01408
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cast-notation-and-introduction-of-safecastltgt"></a>强制转换表示法和 safe_cast 简介&lt;&gt;
强制转换表示法已从托管扩展中的 c + + 更改为 Visual c + +。  
  
 修改现有结构是一种不同且更加困难的体验，比创建初始结构。 有较少的自由度，和解决方案倾向于入理想重新构建和什么是可行下提供现有的结构化依赖项之间的折衷。  
  
 语言扩展是另一个示例。 返回年代初如面向对象的编程变得重要的范例，在 c + + 中的类型安全向下转换设施的需求变得非常迫切。 向下转换是基类指针或对指针引用或派生类的引用的用户显式转换。 向下转换要求显式强制转换。 原因是基类指针的实际类型是运行时; 的一个方面编译器因此无法检查它。 或者，换句话说，向下转换的功能，就像虚拟函数调用，要求某种形式的动态解析。 这就提高了两个问题：  
  
-   为什么应向下转换在需要面向对象的范例？ 虚函数机制是否不足？ 也就是说，为什么无法声明任何需要向下转换 （或任何种类的强制转换） 是设计失败的？  
  
-   为什么应的向下转换为支持 c + + 中的问题？ 毕竟，它不是由 Smalltalk 如面向对象语言中的问题 (或随后，Java 和 C#)？ 什么是它使得支持困难的向下转换功能的 c + + 有关？  
  
 虚函数表示类型的一系列常见依赖于类型的算法。 （我们正在不考虑的接口，它不支持在 ISO c + + 中，但有 CLR 编程中，它代表了有趣的设计替代方法）。 在没有声明的公共接口 （虚函数） 和一组表示应用程序中的实际类型系列具体派生类的抽象基类的类层次结构通常表示该系列的设计域。  
  
 A`Light`层次结构中的计算机生成图像 (CGI) 应用程序域，例如，将具有公共属性，如`color`， `intensity`， `position`， `on`， `off`，依次类推。 可以控制之一多种光源，而不必担心是否特定光源是 spotlight、 定向光源、 非定向光源 （如太阳） 或可能是遮光 light 使用通用接口。 在这种情况下，向下转换为特定的 light-类型以实现其虚拟接口是不必要的。 但是，在生产环境中，速度是重要的。 一个可能向下转换并显式调用每个方法如果这样做内联执行调用可以执行而不是使用虚拟的机制。  
  
 因此，向下转换 c + + 中的一个原因是避免虚拟机制，从而在运行时性能显著提高。 （请注意，此手动优化的自动化 active 研究的区域。 但是，它是更难解决比更换显式使用`register`或`inline`关键字。)  
  
 多态性的双重性质的向下转换回退到另一个原因。 一个办法有助于理解的多态性划分为与被动和动态的成对的窗体中。  
  
 虚调用 （和向下转换功能） 表示动态使用多态性： 一个执行在程序执行过程中该特定实例的基类指针的实际类型所基于的操作。  
  
 将派生的类对象分配给它的基类指针，但是，是一种多态性; 的被动形式它使用多态性作为传输机制。 这是主要使用`Object`，例如，预泛型 CLR 编程中。 当使用被动，基类指针通常选择为传输和存储提供一个接口即太抽象。 `Object`例如，提供大约五种方法通过其接口;任何更具体的行为需要显式向下转换。 例如，如果我们想要调整的角度我们 spotlight 或衰减速率，我们将可以向下转换显式。 内的一系列子类型的虚拟接口实际上不可能成为其多个子级的所有可能的方法的超集，并因此向下转换功能将始终需要一种面向对象语言中。  
  
 如果向下转换安全设施需要使用在面向对象语言中，然后为何未需要 c + + 这么长添加一个？ 问题在于如何提供关于指针的运行时类型的信息。 对于虚拟函数，运行时信息的设置两个部分由编译器：  
  
-   此类对象包含的其他虚拟表指针成员 (在开头或末尾类对象中; 的本身具有有趣的历史记录)，它解决了相应的虚拟表。 例如，spotlight 对象地址 spotlight 虚拟表、 定向光源、 方向浅色虚拟表等  
  
-   每个虚函数具有一个关联固定在表中，槽，要调用的实际实例由存储在表中的地址。 例如，虚拟`Light`析构函数可能与槽 0，相关联`Color`与插槽 1 中，依次类推。 这是高效但不够灵活的策略，因为它在编译时设置和系统开销较小。  
  
 此问题，然后，是如何将类型信息提供给指针而无需更改的 c + + 指针的大小，通过添加第二个地址或直接将添加某种形式的编码类型。 这不是那些程序员 （和程序） 可接受的决定不使用面向对象的范例的仍是主导用户社区。 另一种可能是引入一个特殊的指针，对于多态类类型，但这会令人费解，并且会更难以混合两者，特别是对于指针算术的问题。 它也不会接受维护将每个指针与其当前关联的类型，并动态更新该表相关联的运行时表。  
  
 问题就是有两个用户群体其具有不同但合法的编程要求。 解决方案必须为这两个群体，使得每个其个设想不仅能够进行互操作之间的折衷。 这意味着有可能是不可行的解决方案提供的任何一方和实施解决方案，最后要小于完美。 实际的分辨率围绕多态类定义： 多态类是包含虚拟函数。 多态类支持动态类型安全向下转换。 这解决了维护的指针的作为-地址问题，因为所有多态类都包含到其关联的虚拟表的附加指针成员。 关联的类型信息，因此，可以存储在展开虚拟表结构。 类型安全的向下转换的成本 （几乎） 进行了本地化向用户的工具。  
  
 使用类型安全的向下转换的下一个问题是它的语法。 因为它是强制转换，则提交给的 ISO c + + 委员会的原始建议使用未修饰的 cast 语法，如此示例所示：  
  
```  
spot = ( SpotLight* ) plight;  
```  
  
 但是，这被拒绝由委员会，因为它不允许用户控制的成本的强制转换。 如果动态类型安全向下转换具有相同的语法与以前不安全且静态强制转换表示法，则它将为一种替代物，并且用户具有不能为空时它是不必要和可能过于昂贵禁止运行时开销。  
  
 一般情况下，c + + 中没有始终进行禁止显示编译器支持的功能所依据的机制。 例如，我们可以关闭虚拟机制通过使用类范围运算符 (`Box::rotate(angle)`) 或通过调用虚方法的类对象 （而不是指针或引用该类的）。 此后一种取消不需要的语言，但很实现问题，类似于形式的声明中的一个临时构造的抑制质量：  
  
```  
// compilers are free to optimize away the temporary  
X x = X::X( 10 );  
```  
  
 因此建议被退回以进行进一步考虑，并考虑了几个备选的表示法，返回给委员会了窗体 (`?type`)，这指示它的不确定性-即动态性。 这使得用户能够-静态或动态-这两种形式之间切换但没有与之太高兴。 因此回从头开始。 第三个和成功的表示法是现在标准`dynamic_cast<type>`，它被推广为一组的四个新样式强制转换表示法。  
  
 ISO c + + 中`dynamic_cast`返回`0`时应用于不适当的指针类型，并引发`std::bad_cast`异常时应用于引用类型。 在 c + + 托管扩展应用`dynamic_cast`指向托管的引用类型 （由于其指针表示形式） 始终返回`0`。 `__try_cast<type>`在中引入了模拟作为异常抛出变体`dynamic_cast`，只不过它将引发`System::InvalidCastException`如果转换失败。  
  
```  
public __gc class ItemVerb;  
public __gc class ItemVerbCollection {  
public:  
   ItemVerb *EnsureVerbArray() [] {  
      return __try_cast<ItemVerb *[]>  
         (verbList->ToArray(__typeof(ItemVerb *)));  
   }  
};  
```  
  
 在新语法中，`__try_cast`已将转换为`safe_cast`。 下面是相同的代码段的新语法中：  
  
```  
public ref class ItemVerb;  
public ref class ItemVerbCollection {  
public:  
   array<ItemVerb^>^ EnsureVerbArray() {  
      return safe_cast<array<ItemVerb^>^>  
         ( verbList->ToArray( ItemVerb::typeid ));  
   }  
};  
```  
  
 在托管领域中，很重要，以便通过限制的程序员的能力的方式将代码保留无法验证的类型之间强制转换为可验证代码。 这是由新语法的动态编程范例的一个重要方面。 出于此原因，旧样式强制转换的实例重新强制转换内部为运行时强制转换，因此，例如：  
  
```  
// internally recast into the   
// equivalent safe_cast expression above  
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );   
```  
  
 另一方面，由于多态性提供主动模式和被动模式，因此，有时执行向下转换只是为了获取访问权限的子类型的非虚拟 API 所需。 发生这种情况，例如，与类的成员，待解决任何类型在层次结构中 （作为传输机制被动多态性），但在特定的程序的上下文中的实际实例已知的。 在这种情况下，具有的运行时检查的强制转换可以是不可接受的开销。 如果新的语法是作为编程语言的托管系统，它必须提供几种可编译时间 (即，静态) 向下转换。 这就是为什么的应用程序`static_cast`允许保持编译时向下转换表示法：  
  
```  
// ok: cast performed at compile-time.   
// No run-time check for type correctness  
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));  
```  
  
 问题是没有办法保证执行程序员`static_cast`是正确而且善意; 也就是说，没有方法来强制是可验证的托管的代码。 这是一个更加急迫问题的情况下动态程序比在纯模式、 但并不足够编程语言不允许用户能够静态和运行时强制转换之间切换系统中。  
  
 存在但是是性能陷阱和的新语法中的缺陷。 在本机编程中，没有旧样式强制转换表示法和将新样式之间没有性能差异`static_cast`表示法。 但在新语法中，旧样式强制转换表示法是比将新样式利用贵很多`static_cast`表示法。 原因是编译器内部转换使用转换将引发异常的运行时检查的旧样式表示法。 此外，它还改变代码的执行配置文件因为它会导致未捕获的异常，使应用程序停止运行-可能是这样做是明智的但相同的错误不会导致该异常如果`static_cast`使用表示法。 有人可能会说这将促使用户使用新式的表示法。 而只在失败; 时否则，它将导致使用旧样式表示法来运行速度显著变慢没有可见的原因，理解的程序类似于以下 C 程序员缺陷：  
  
```  
// pitfall # 1:   
// initialization can remove a temporary class object,   
// assignment cannot  
Matrix m;  
m = another_matrix;  
  
// pitfall # 2: declaration of class objects far from their use  
Matrix m( 2000, 2000 ), n( 2000, 2000 );  
if ( ! mumble ) return;  
```  
  
## <a name="see-also"></a>请参阅  
 [常规语言更改 (C + + /cli CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [/Clr 下的 C 样式强制转换 (C + + /cli CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)