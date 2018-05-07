---
title: 值类型语义 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
- virtual functions, value types
- inheritance, value types
- pinning pointers
- pin_ptr keyword [C++]
- __pin keyword
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 44662f2ad8e79712b4aab17e2784a72e01ec4116
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="value-type-semantics"></a>值类型语义
值类型语义已从托管扩展中的 c + + 更改为 Visual c + +。  
  
 下面是所使用的托管扩展的 c + + 规范的规范的简单值类型：  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
```  
  
 在托管扩展中，我们可以具有值类型的四个语法变的体 （位置 2 和 3 的窗体相同语义上）：  
  
```  
V v = { 0 };       // Form (1)  
V *pv = 0;         // Form (2) an implicit form of (3)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0; // Form (4) must be local   
```  
  
## <a name="invoking-inherited-virtual-methods"></a>调用继承的虚方法  
 `Form (1)` 是规范化的值对象，并且它很好地理解，除了当有人尝试调用继承的虚方法，如`ToString()`。 例如：  
  
```  
v.ToString(); // error!  
```  
  
 由于不重写中调用此方法，以便`V`，编译器必须有权访问基类的关联的虚拟表。 由于值类型是在状态存储，没有指向其虚拟表 (vptr) 相关的指针，这种方式要求`v`进行装箱。 在托管扩展语言设计中，隐式装箱不支持，但必须通过显式指定程序员，如  
  
```  
__box( v )->ToString(); // Managed Extensions: note the arrow  
```  
  
 这种设计的主要目的是教学： 基础机制必须是对程序员可见，以便她将了解不提供在她值类型实例的成本。 已`V`要包含的实例`ToString`，装箱不是必需。  
  
 新语法中删除的显式装箱对象，但不是本身，装箱的基础成本词法复杂性：  
  
```  
v.ToString(); // new syntax  
```  
  
 但这样可能会误导类设计器并不具有提供的显式实例的成本`ToString`方法内的`V`。 首选隐式装箱的原因是虽然通常只有一个类设计器，有无限的数量的用户，他们不将能自由地修改`V`以消除可能导致重大开销显式装箱。  
  
 用于确定是否提供一个重写实例条件`ToString`值中类应该的频率和其使用位置。 如果它调用极少数情况下，是当然没什么好处，其定义。 同样，如果是非性能方面的应用程序调用它，则将其添加将也不会显著提高将添加到应用程序的常规性能。 或者，一个可以为装箱的值，保留的跟踪句柄并通过该句柄调用者不需要装箱。  
  
## <a name="there-is-no-longer-a-value-class-default-constructor"></a>不再值类默认构造函数  
 值类型的托管扩展和新的语法之间的另一个差异是支持的因为删除了对默认构造函数。 这是因为有在其中 CLR 可以但不调用关联的默认构造函数创建值类型的实例的执行期间的情况。 也就是说，尝试在托管扩展中支持在值类型的默认构造函数无法不在实践中得到保证。 给定保证的它被认为更好，若要完全删除支持，而不是让它变得不确定在其应用程序中。  
  
 这不是最初，这可能看起来像糟糕。 这是因为值类型的每个对象自动清空 （即，每种类型初始化为其默认值）。 因此，本地实例的成员永远不会不确定。 在这个意义上，并不真正丢失根本-和实际上是由 CLR 执行时效率更高定义普通的默认构造函数的功能丢失。  
  
 托管扩展的用户定义的非普通的默认构造函数时问题。 这不具有映射到新的语法。 构造函数中的代码将需要迁移到将需要显式调用由用户命名的初始化方法。  
  
 否则保持不变值类型对象的新语法中的声明。 这样做的缺点在于，值类型没有令人满意的本机类型换行原因如下：  
  
-   没有支持在值类型的析构函数。 也就是说，没有方法来自动执行一组由对象的生存期结束时的触发的操作。  
  
-   本机类可以包含仅在托管类型中作为指针，然后在本机堆上分配。  
  
 我们想要包装在值类型而不是引用类型以避免双堆分配的小型本机类： 本机堆来保存的本机类型和 CLR 堆来保存的托管的包装。 包装在值类型的本机类，你可以避免托管的堆中，但它无法自动执行在回收的本机堆内存。 引用类型是在其中非普通的本机类进行简单包装唯一可行的托管的类型。  
  
## <a name="interior-pointers"></a>内部指针  
 `Form (2)` 和`Form (3)`更高版本可以解决此领域或下一个 （也就是说，任何托管或本机类型） 中几乎任何类型。 因此，例如，以下所有允许在托管扩展中：  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
  
V v = { 0 };  // Form (1)  
V *pv = 0;  // Form (2)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0;  // Form (4)  
  
R* r;  
  
pv = &v;            // address a value type on the stack  
pv = __nogc new V;  // address a value type on native heap  
pv = pvgc;          // we are not sure what this addresses  
pv = pvbx;          // address a boxed value type on managed heap  
pv = &r->vr;        // an interior pointer to value type within a  
                    //    reference type on the managed heap  
```  
  
 因此，`V*`可以解决本地块内的位置 （并因此可以无关联），在全局范围内，在本机堆 （例如，如果其所寻址的对象已被删除），CLR 堆内 （并且因此将跟踪如果它应进行重新定位在垃圾回收期间），并在 CLR 堆 （内部指针，如这称为，还以透明方式跟踪） 上的引用对象的内部。  
  
 在托管扩展中，没有方法以分隔出的本机方面`V*`; 即，它处理是在其 （含），可处理它寻址的对象或托管堆上的子对象的可能性。  
  
 在新语法中，值类型指针计入两种类型： `V*`，这是限制为非 CLR 堆位置和内部指针， `interior_ptr<V>`，它允许但不需要在托管堆中的地址。  
  
```  
// may not address within managed heap   
V *pv = 0;   
  
// may or may not address within managed heap  
interior_ptr<V> pvgc = nullptr;   
```  
  
 `Form (2)` 和`Form (3)`的托管扩展将映射到`interior_ptr<V>`。 `Form (4)` 是一个跟踪句柄。 它解决了在托管堆中具有已装箱的整个对象。 对其进行转换到的新语法中`V^`，  
  
```  
V^ pvbx = nullptr; // __box V* pvbx = 0;    
```  
  
 所有映射到的新语法中的内部指针的托管扩展中的以下声明。 (它们是值类型中的`System`命名空间。)  
  
```  
Int32 *pi;   // => interior_ptr<Int32> pi;  
Boolean *pb; // => interior_ptr<Boolean> pb;  
E *pe;       // => interior_ptr<E> pe; // Enumeration  
```  
  
 内置类型不被认为是托管的类型，尽管它们是否作为别名中的类型`System`命名空间。 因此以下映射真的托管扩展和新的语法之间：  
  
```  
int * pi;     // => int* pi;  
int __gc * pi2; // => interior_ptr<int> pi2;  
```  
  
 转换时`V*`现有程序，在最保守的策略是始终将它转换为`interior_ptr<V>`。 这是在托管扩展中已处理方式。 在新语法中，程序员可以将值类型限制为非托管堆地址时，通过指定的选项`V*`而不是内部指针。 如果在转换程序时，可以执行它使用的所有可传递闭包，请确保所有分配的地址均位于托管堆，则可以将保留其作为`V*`属正常情况。  
  
## <a name="pinning-pointers"></a>钉住指针  
 垃圾回收器可能会根据需要移动通常在压缩阶段驻留在堆中中的其他位置到 CLR 堆的对象。 此移动不是问题跟踪句柄、 跟踪引用和内部指针以透明方式来更新这些实体。 此移动是一个问题，但是，如果用户已通过在运行时环境之外的 CLR 堆上对象的地址。 在这种情况下，该对象的可变移动是有可能会导致运行时失败。 对这些移动，我们必须本地将它们固定到其位置以便其外部使用的范围中免除对象。  
  
 在托管扩展中，*钉住指针*来限定指针声明与声明`__pin`关键字。 下面是从托管扩展规范稍许修改示例：  
  
```  
__gc struct H { int j; };  
  
int main()   
{  
   H * h = new H;  
   int __pin * k = & h -> j;  
  
   // ...  
};  
```  
  
 在新的语言设计中，语法类似于内部指针声明钉住指针。  
  
```  
ref struct H  
{  
public:  
   int j;  
};  
  
int main()  
{  
   H^ h = gcnew H;  
   pin_ptr<int> k = &h->j;  
  
   // ...  
}  
```  
  
 在新语法中钉住指针是一个内部指针的特殊情况。 钉住指针原始约束保持状态。 例如，它不能用作参数或返回类型的方法;它可以仅在本地对象上声明。 多个附加约束，但是，已添加的新语法中。  
  
 钉住指针的默认值是`nullptr`，而不`0`。 A`pin_ptr<>`无法初始化或分配`0`。 所有分配的`0`现有代码中将需要更改为`nullptr`。  
  
 在托管扩展中钉住指针在于允许进行寻址的完整对象，如下面的示例摘自托管扩展规范中所示：  
  
```  
__gc class G {  
public:  
   void incr(int* pi) { pi += 1; }  
};  
__gc struct H { int j; };  
void f( G * g ) {  
   H __pin * pH = new H;     
   g->incr(& pH -> j);     
};  
```  
  
 在新语法中，固定整个对象返回的`new`不支持表达式。 相反，内部成员的地址需要钉住。 例如，应用于对象的  
  
```  
ref class G {  
public:  
   void incr(int* pi) { *pi += 1; }  
};  
ref struct H { int j; };  
void f( G^ g ) {  
   H ^ph = gcnew H;  
   Console::WriteLine(ph->j);  
   pin_ptr<int> pj = &ph->j;  
   g->incr(  pj );  
   Console::WriteLine(ph->j);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [值类型和它们的行为 (C + + /cli CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)   
 [interior_ptr (C + + /cli CLI)](../windows/interior-ptr-cpp-cli.md)   
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)