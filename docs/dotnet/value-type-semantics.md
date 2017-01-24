---
title: "值类型语义 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__pin 关键字"
  - "继承, 值类型"
  - "interior_ptr 关键字 [C++]"
  - "pin_ptr 关键字 [C++]"
  - "钉住指针"
  - "虚函数, 值类型"
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 值类型语义
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从 C\+\+ 托管扩展到 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]，值类型的语义已发生更改。  
  
 下面是 C\+\+ 托管扩展规范中使用的规范化的简单值类型：  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
```  
  
 在托管扩展中，值类型有四个语法变体（其中形式 2 和 3 语义相同）：  
  
```  
V v = { 0 };       // Form (1)  
V *pv = 0;         // Form (2) an implicit form of (3)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0; // Form (4) must be local   
```  
  
## 调用所继承的虚方法  
 `Form (1)` 是规范化的值对象，并且相当容易理解，但在尝试调用继承而来的虚方法（如 `ToString()`）时除外。  例如：  
  
```  
v.ToString(); // error!  
```  
  
 由于此方法在 `V` 中没有重写，因此，为了调用此方法，编译器必须具有访问基类的关联虚表的权限。  由于值类型是状态内存储，没有指向其虚表 \(vptr\) 的关联指针，因此需要对 `v` 进行装箱。  在托管扩展语言设计中，不支持隐式装箱，但它必须由程序员显式指定，如下所示：  
  
```  
__box( v )->ToString(); // Managed Extensions: note the arrow  
```  
  
 这种设计的主要目的是教学：它旨在使基础机制对程序员可见，以便程序员了解不在值类型内提供实例的“代价”。  如果 `V` 包含 `ToString` 的实例，则没有必要装箱。  
  
 在新语法中，移除了显式将对象进行装箱的词法复杂性，而不是装箱本身的基本开销：  
  
```  
v.ToString(); // new syntax  
```  
  
 但是，由于没有在 `V` 内提供 `ToString` 方法的显式实例，这样可能会误导类设计器。  首选隐式装箱的原因经常是：通常只有一个类设计器，虽然用户数不受限制，但他们都不能自由修改 `V` 以消除可能导致重大开销的显式装箱。  
  
 确定是否在值类内提供 `ToString` 的重写实例的标准应是该实例使用的频率和位置。  如果很少调用该实例，定义它当然没有太多优点。  同样，如果在应用程序的与性能无关的区域调用该实例，添加它也不会显著提高应用程序的常规性能。  或者，可以将跟踪句柄保持为装箱值，通过该句柄的调用将不需要装箱。  
  
## 不再存在值类默认构造函数  
 托管扩展和新语法之间的值类型的另一个差异是移除了对默认构造函数的支持。  这是因为在执行过程的某些情况下，CLR 可以在不调用关联的默认构造函数的情况下，创建值类型的实例。  即，在托管扩展下，尝试支持值类型内的默认构造函数实际上未能得到保证。  在不能得到保证的情况下，最好完全删除支持，而不是使其在应用程序中变得不确定。  
  
 这至少不会像最初看起来那样糟糕。  这是因为值类型的每个对象会自动被赋予零值（即，每个类型都初始化为其默认值）。  结果是，永不取消本地实例的成员定义。  从这种意义上来说，不能定义常用的默认构造函数根本不是一种损失 — 事实上，如果由 CLR 执行将更为有效。  
  
 问题出现在托管扩展用户定义非常用的默认构造函数时。  此时，没有到新语法的映射。  构造函数内的代码需要迁移到一个命名初始化方法中，然后需要由用户来显式调用该方法。  
  
 否则，新语法内值类型对象的声明不会更改。  这样做的缺点是：由于下列原因，值类型对本机类型的包装具有以下缺陷：  
  
-   不支持值类型内的析构函数。  也就是说，无法自动化由对象的生存期结束而触发的一组操作。  
  
-   本机类只能作为指针包含在托管类型内，然后在本机堆上分配该指针。  
  
 我们希望在值类型（而不是引用类型）中包装小的本机类，以避免双堆分配：本机堆保存本机类型，而 CLR 堆保存托管包装。  在值类型内包装本机类使您可以避免托管堆，但它无法自动回收本机堆内存。  引用类型是可在其中包装非常用本机类的唯一可行的托管类型。  
  
## 内部指针  
 上面的 `Form (2)` 和 `Form (3)` 可以解决此领域或下一领域中的几乎任何类型（也就是说，任何托管类型或本机类型）。  例如，托管扩展中允许以下所有类型：  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
  
V v = { 0 };  // Form (1)  
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
  
 因此，`V*` 可以对以下各项中的一个位置进行寻址：全局范围内某局部块（因此，可为虚的）、本机堆（例如，如果它寻址的对象已被删除）、CLR 堆（因此，如果在垃圾回收期间应对它进行重新定位，它将被跟踪）以及 CLR 堆上引用对象的内部（内部指针，在调用它时，它也被透明跟踪）。  
  
 在托管扩展中，无法分离出 `V*` 的本机方面；也就是说，在它包含的方面对其进行处理，该包含的方面处理它在托管堆上寻址对象或子对象的可能性。  
  
 在新语法中，值类型指针分为两种类型：`V*`（限于非 CLR 堆位置）和内部指针 `interior_ptr<V>`（允许但不要求托管堆内的地址）。  
  
```  
// may not address within managed heap   
V *pv = 0;   
  
// may or may not address within managed heap  
interior_ptr<V> pvgc = nullptr;   
```  
  
 托管扩展的 `Form (2)` 和 `Form (3)` 映射到 `interior_ptr<V>`。  `Form (4)` 是跟踪句柄。  它寻址已在托管堆内装箱的整个对象。  在新语法中，它转换为 `V^`，  
  
```  
V^ pvbx = nullptr; // __box V* pvbx = 0;    
```  
  
 托管扩展中的下列声明全部映射到新语法中的内部指针。（它们是 `System` 命名空间内的值类型。）  
  
```  
Int32 *pi;   // => interior_ptr<Int32> pi;  
Boolean *pb; // => interior_ptr<Boolean> pb;  
E *pe;       // => interior_ptr<E> pe; // Enumeration  
```  
  
 内置类型不被认为是托管类型，尽管它们确实在 `System` 命名空间内作为类型的别名。  因此，以下映射在托管扩展和新语法之间仍是成立的：  
  
```  
int * pi;     // => int* pi;  
int __gc * pi2; // => interior_ptr<int> pi2;  
```  
  
 在现有程序中转换 `V*` 时，最保守的策略是始终将它转换为 `interior_ptr<V>`。  这是它在托管扩展下的处理方式。  在新语法中，程序员可以选择通过指定 `V*` 而不是内部指针，将值类型限制为非托管堆地址。  在转换程序时，如果您可以执行它使用的所有可传递闭包，并确信所有已分配的地址均位于托管堆之外，则可以将其保留为 `V*`。  
  
## 钉住指针  
 通常，在压缩阶段，垃圾回收器可选择将驻留在 CLR 堆上的对象移动到堆内的不同位置。  这种移动对于跟踪句柄、跟踪引用和内部指针而言不是问题，它们都透明地更新这些实体。  但是，如果用户在运行时环境外传递了 CLR 堆上对象的地址，这种移动就会导致问题。  在这种情况下，对象的不稳定运动可能导致运行时失败。  要避免此类对象的移动，必须在本地将它们钉在自己的位置上以供外部使用。  
  
 在托管扩展中，“钉住指针”是通过使用 `__pin` 关键字限定指针声明来声明的。  下面是一个来自托管扩展规范的经过略微修改的示例：  
  
```  
__gc struct H { int j; };  
  
int main()   
{  
   H * h = new H;  
   int __pin * k = & h -> j;  
  
   // …  
};  
```  
  
 在新的语言设计中，钉住指针是使用类似于内部指针的语法来声明的。  
  
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
  
   // …  
}  
```  
  
 新语法下的钉住指针是内部指针的一个特例。  钉住指针的原始约束仍然保留。  例如，它不能用作方法的参数或返回类型；它只能在局部对象上声明。  但是，新语法中添加了多个附加约束。  
  
 钉住指针的默认值是 `nullptr`，而不是 `0`。  不能对 `pin_ptr<>` 初始化或赋予 `0`。  现有代码中所有赋予 `0` 的语句都需要更改为 `nullptr`。  
  
 在托管扩展下，允许使用钉住指针来寻址整个对象，如以下来自托管扩展规范的示例所示：  
  
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
  
 在新语法中，不支持钉住由 `new` 表达式返回的整个对象。  相反，需要钉住内部成员的地址。  例如，  
  
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
  
## 请参阅  
 [值类型及其行为 \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md)   
 [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)   
 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md)