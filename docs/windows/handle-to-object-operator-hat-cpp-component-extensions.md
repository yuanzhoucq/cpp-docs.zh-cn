---
title: 对象句柄运算符 (^) （c + + 组件扩展） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ^ handle to object [C++]
ms.assetid: 70c411e6-be57-4468-a944-6ea7be89f392
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc55ab1dad4ee9ba088aaae92f76e58b29683b29
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569799"
---
# <a name="handle-to-object-operator---c-component-extensions"></a>对象句柄运算符 (^)（C++ 组件扩展）
*句柄声明符*(`^`，发音为"hat")，修改类型[说明符](../cpp/overview-of-declarators.md)表示声明的对象将自动删除该系统确定该对象是无法再进行访问。  
  
## <a name="accessing-the-declared-object"></a>访问声明的对象  
 使用句柄声明符声明的变量与指向对象的指针具有类似的行为。 但是，该变量指向整个对象，不能指向对象的某个成员，也不支持指针算法。 可使用间接寻扯运算符 (`*`) 访问对象，使用箭头成员访问运算符 (`->`) 访问对象的成员。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 编译器使用 COM*引用计数*机制来确定是否对象不再使用，并且可以删除。 因为从 Windows 运行时接口派生的对象实际上是 COM 对象，所以这是可行的。 在创建或复制对象时，引用计数会递增；当对象设置为 null 或超出范围时，引用计数会递减。 如果引用计数归零，将立即自动删除对象。  
  
 句柄声明符的优点在于，在 COM 中，您必须以显式方式管理对象的引用计数，而这个过程单调乏味又容易出错。 也就是说，要递增或递减引用计数，必须调用对象的 AddRef() 和 Release() 方法。 但是，如果使用对象声明符声明一个对象，则 Visual C++ 编译器会生成自动调整引用计数的代码。  
  
 有关如何实例化对象的信息，请参阅[ref 新](../windows/ref-new-gcnew-cpp-component-extensions.md)。  
  
## <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 系统使用 CLR*垃圾回收器*机制来确定是否对象不再使用，并且可以删除。 公共语言运行时会维护一个用来分配对象的堆，并在程序中使用托管引用（变量）来指示对象在堆上的位置。 当不再使用某个对象时，会释放它在堆上占用的内存。 垃圾回收器会定期压缩该堆，已更好地利用释放的内存。 压缩堆可能会移动堆上的对象，这会使托管引用所引用的位置不再有效。 但是，垃圾回收器知道所有托管引用的位置，并会自动更新位置来指示对象在堆上的当前位置。  
  
 因为本机 C++ 指针 (`*`) 和引用 (`&`) 都是托管引用，所以垃圾回收器不能更新它们指向的地址。 若要解决此问题，请使用句柄声明符指定一个变量，垃圾回收器能够知道这个变量的状态并会自动进行更新。  
  
 在 Visual C++ 2002 和 Visual C++ 2003 中，使用 `__gc *` 来声明托管堆上的对象。  在新的语法中，`^` 取代了 `__gc *`。  
  
 有关详细信息，请参阅[如何： 在本机类型中声明处理](../dotnet/how-to-declare-handles-in-native-types.md)。  
  
### <a name="examples"></a>示例  
 **示例**  
  
 此示例演示如何在托管堆上创建引用类型的实例。  此示例还演示，您可以使用一个句柄初始化另一个句柄，使两个引用都指向垃圾回收托管堆上的同一对象。 请注意，该分配[nullptr](../windows/nullptr-cpp-component-extensions.md)到一个句柄不会将标记为垃圾回收的对象。  
  
```cpp  
// mcppv2_handle.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   MyClass() : i(){}  
   int i;  
   void Test() {  
      i++;  
      System::Console::WriteLine(i);  
   }  
};  
  
int main() {  
   MyClass ^ p_MyClass = gcnew MyClass;  
   p_MyClass->Test();  
  
   MyClass ^ p_MyClass2;  
   p_MyClass2 = p_MyClass;  
  
   p_MyClass = nullptr;  
   p_MyClass2->Test();     
}  
```  
  
 **输出**  
  
```Output  
1  
2  
```  
  
 **示例**  
  
 以下示例演示如何声明一个句柄，指向托管堆上的一个对象，而对象的类型是装箱值类型。 示例还演示如何从装箱对象获取值类型。  
  
```cpp  
// mcppv2_handle_2.cpp  
// compile with: /clr  
using namespace System;  
  
void Test(Object^ o) {  
   Int32^ i = dynamic_cast<Int32^>(o);  
  
   if(i)  
      Console::WriteLine(i);  
   else  
      Console::WriteLine("Not a boxed int");  
}  
  
int main() {  
   String^ str = "test";  
   Test(str);  
  
   int n = 100;  
   Test(n);  
}  
```  
  
 **输出**  
  
```Output  
Not a boxed int  
100  
```  
  
 **示例**  
  
 此示例演示，如何将使用 void* 指针指向任意对象的常见 C++ 思路替换为使用 Object^，后者可以容纳指向任意引用类的句柄。 它还演示可将所有类型（如数组和委托）都转换为对象句柄。  
  
```cpp  
// mcppv2_handle_3.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Collections;  
public delegate void MyDel();  
ref class MyClass {  
public:  
   void Test() {}  
};  
  
void Test(Object ^ x) {  
   Console::WriteLine("Type is {0}", x->GetType());  
}  
  
int main() {  
   // handle to Object can hold any ref type  
   Object ^ h_MyClass = gcnew MyClass;  
  
   ArrayList ^ arr = gcnew ArrayList();  
   arr->Add(gcnew MyClass);  
  
   h_MyClass = dynamic_cast<MyClass ^>(arr[0]);  
   Test(arr);  
  
   Int32 ^ bi = 1;  
   Test(bi);  
  
   MyClass ^ h_MyClass2 = gcnew MyClass;  
  
   MyDel^ DelInst = gcnew MyDel(h_MyClass2, &MyClass::Test);  
   Test(DelInst);  
}  
```  
  
 **输出**  
  
```Output  
Type is System.Collections.ArrayList  
  
Type is System.Int32  
  
Type is MyDel  
```  
  
 **示例**  
  
 此示例演示可以对句柄取消引用，并通过取消引用的句柄访问成员。  
  
```cpp  
// mcppv2_handle_4.cpp  
// compile with: /clr  
using namespace System;  
value struct DataCollection {  
private:  
   int Size;  
   array<String^>^ x;  
  
public:  
   DataCollection(int i) : Size(i) {  
      x = gcnew array<String^>(Size);  
      for (int i = 0 ; i < Size ; i++)  
         x[i] = i.ToString();  
   }  
  
   void f(int Item) {  
      if (Item >= Size)  
      {  
         System::Console::WriteLine("Cannot access array element {0}, size is {1}", Item, Size);  
         return;  
      }  
      else  
         System::Console::WriteLine("Array value: {0}", x[Item]);  
   }  
};  
  
void f(DataCollection y, int Item) {  
   y.f(Item);  
}  
  
int main() {  
   DataCollection ^ a = gcnew DataCollection(10);  
   f(*a, 7);   // dereference a handle, return handle's object  
   (*a).f(11);   // access member via dereferenced handle  
}  
```  
  
 **输出**  
  
```Output  
Array value: 7  
  
Cannot access array element 11, size is 10  
```  
  
 **示例**  
  
 此示例演示不能将本机引用 (`&`) 绑定到托管类型的 `int` 成员，因为 `int` 可能存储在垃圾回收堆中，但本机引用不能跟踪托管堆中的对象移动。 解决方法是使用局部变量，或将 `&` 更改为 `%`，使它成为跟踪引用。  
  
```cpp  
// mcppv2_handle_5.cpp  
// compile with: /clr  
ref struct A {  
   void Test(unsigned int &){}  
   void Test2(unsigned int %){}  
   unsigned int i;  
};  
  
int main() {  
   A a;  
   a.i = 9;  
   a.Test(a.i);   // C2664  
   a.Test2(a.i);   // OK  
  
   unsigned int j = 0;  
   a.Test(j);   // OK  
}  
```  
  
### <a name="requirements"></a>要求  
 编译器选项：`/clr`  
  
## <a name="see-also"></a>请参阅  
 [运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)   
 [跟踪引用运算符](../windows/tracking-reference-operator-cpp-component-extensions.md)