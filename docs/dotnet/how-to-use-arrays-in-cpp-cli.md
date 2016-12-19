---
title: "如何：在 C++/CLI 中使用数组 | Microsoft Docs"
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
  - "数组 [C++], 单维"
ms.assetid: 301cfb3e-199f-42c8-8151-629dce9e87f3
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 C++/CLI 中使用数组
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文介绍 [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)]如何使用数组。  
  
## 一维数组  
 下面的示例演示如何创建单维数组的引用、值和本机指针类型。  它还演示如何从函数返回的单维数组以及如何传递一维数组作为参数传递给函数。  
  
```  
// mcppv2_sdarrays.cpp  
// compile with: /clr  
using namespace System;  
  
#define ARRAY_SIZE 2  
  
value struct MyStruct {  
   int m_i;  
};  
  
ref class MyClass {  
public:  
   int m_i;  
};  
  
struct MyNativeClass {  
   int m_i;  
};  
  
// Returns a managed array of a reference type.  
array<MyClass^>^ Test0() {  
   int i;  
   array< MyClass^ >^ local = gcnew array< MyClass^ >(ARRAY_SIZE);  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++) {  
      local[i] = gcnew MyClass;  
      local[i] -> m_i = i;  
   }  
   return local;  
}  
  
// Returns a managed array of Int32.  
array<Int32>^ Test1() {  
   int i;  
   array< Int32 >^ local = gcnew array< Int32 >(ARRAY_SIZE);  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++)  
      local[i] = i + 10;  
   return local;  
}  
  
// Modifies an array.  
void Test2(array< MyNativeClass * >^ local) {  
   for (int i = 0 ; i < ARRAY_SIZE ; i++)  
      local[i] -> m_i = local[i] -> m_i + 2;  
}  
  
int main() {  
   int i;  
  
   // Declares an array of user-defined reference types  
   // and uses a function to initialize.  
   array< MyClass^ >^ MyClass0;  
   MyClass0 = Test0();  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++)  
      Console::WriteLine("MyClass0[{0}] = {1}", i, MyClass0[i] -> m_i);  
   Console::WriteLine();  
  
   // Declares an array of value types and uses a function to initialize.  
   array< Int32 >^ IntArray;  
   IntArray = Test1();  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++)  
      Console::WriteLine("IntArray[{0}] = {1}", i, IntArray[i]);  
   Console::WriteLine();  
  
   // Declares and initializes an array of user-defined   
   // reference types.  
   array< MyClass^ >^ MyClass1 = gcnew array< MyClass^ >(ARRAY_SIZE);  
   for (i = 0 ; i < ARRAY_SIZE ; i++) {  
      MyClass1[i] = gcnew MyClass;  
      MyClass1[i] -> m_i = i + 20;  
   }  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++)  
      Console::WriteLine("MyClass1[{0}] = {1}", i, MyClass1[i] -> m_i);  
   Console::WriteLine();  
  
   // Declares and initializes an array of pointers to a native type.  
   array< MyNativeClass * >^ MyClass2 = gcnew array<   
      MyNativeClass * >(ARRAY_SIZE);  
   for (i = 0 ; i < ARRAY_SIZE ; i++) {  
      MyClass2[i] = new MyNativeClass();  
      MyClass2[i] -> m_i = i + 30;  
   }  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++)  
      Console::WriteLine("MyClass2[{0}] = {1}", i, MyClass2[i]->m_i);  
   Console::WriteLine();  
  
   Test2(MyClass2);  
   for (i = 0 ; i < ARRAY_SIZE ; i++)  
      Console::WriteLine("MyClass2[{0}] = {1}", i, MyClass2[i]->m_i);  
   Console::WriteLine();  
  
   delete[] MyClass2[0];  
   delete[] MyClass2[1];  
  
   // Declares and initializes an array of user-defined value types.  
   array< MyStruct >^ MyStruct1 = gcnew array< MyStruct >(ARRAY_SIZE);  
   for (i = 0 ; i < ARRAY_SIZE ; i++) {  
      MyStruct1[i] = MyStruct();  
      MyStruct1[i].m_i = i + 40;  
   }  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++)  
      Console::WriteLine("MyStruct1[{0}] = {1}", i, MyStruct1[i].m_i);  
}  
  
```  
  
 **Output**  
  
  **MyClass0\[0\] \= 0**  
**MyClass0\[1\] \= 1**  
**IntArray\[0\] \= 10**  
**IntArray\[1\] \= 11**  
**MyClass1\[0\] \= 20**  
**MyClass1\[1\] \= 21**  
**MyClass2\[0\] \= 30**  
**MyClass2\[1\] \= 31**  
**MyClass2\[0\] \= 32**  
**MyClass2\[1\] \= 33**  
**MyStruct1\[0\] \= 40**  
**MyStruct1\[1\] \= 41** 下一个示例显示如何对一维托管数组初始化的聚合。  
  
```  
// mcppv2_sdarrays_aggregate_init.cpp  
// compile with: /clr  
using namespace System;  
  
ref class G {  
public:  
   G(int i) {}  
};  
  
value class V {  
public:  
   V(int i) {}  
};  
  
class N {  
public:  
   N(int i) {}  
};  
  
int main() {  
   // Aggregate initialize a single-dimension managed array.  
   array<String^>^ gc1 = gcnew array<String^>{"one", "two", "three"};  
   array<String^>^ gc2 = {"one", "two", "three"};  
  
   array<G^>^ gc3 = gcnew array<G^>{gcnew G(0), gcnew G(1), gcnew G(2)};  
   array<G^>^ gc4 = {gcnew G(0), gcnew G(1), gcnew G(2)};     
  
   array<Int32>^ value1 = gcnew array<Int32>{0, 1, 2};  
   array<Int32>^ value2 = {0, 1, 2};  
  
   array<V>^ value3 = gcnew array<V>{V(0), V(1), V(2)};  
   array<V>^ value4 = {V(0), V(1), V(2)};  
  
   array<N*>^ native1 = gcnew array<N*>{new N(0), new N(1), new N(2)};  
   array<N*>^ native2 = {new N(0), new N(1), new N(2)};  
}  
  
```  
  
 **Output**  
  
  **MyClass0\[0, 0\] \= 0**  
**MyClass0\[0, 1\] \= 0**  
**MyClass0\[1, 0\] \= 1**  
**MyClass0\[1, 1\] \= 1**  
**IntArray\[0, 0\] \= 10**  
**IntArray\[0, 1\] \= 10**  
**IntArray\[1, 0\] \= 11**  
**IntArray\[1, 1\] \= 11** 此示例演示如何在多维托管数组上执行聚合初始化：  
  
```  
// mcppv2_mdarrays_aggregate_initialization.cpp  
// compile with: /clr  
using namespace System;  
  
ref class G {  
public:  
   G(int i) {}  
};  
  
value class V {  
public:  
   V(int i) {}  
};  
  
class N {  
public:  
   N(int i) {}  
};  
  
int main() {  
   // Aggregate initialize a multidimension managed array.  
   array<String^, 2>^ gc1 = gcnew array<String^, 2>{ {"one", "two"},   
       {"three", "four"} };  
   array<String^, 2>^ gc2 = { {"one", "two"}, {"three", "four"} };  
  
   array<G^, 2>^ gc3 = gcnew array<G^, 2>{ {gcnew G(0), gcnew G(1)},   
       {gcnew G(2), gcnew G(3)} };  
   array<G^, 2>^ gc4 = { {gcnew G(0), gcnew G(1)}, {gcnew G(2), gcnew G(3)} };  
  
   array<Int32, 2>^ value1 = gcnew array<Int32, 2>{ {0, 1}, {2, 3} };  
   array<Int32, 2>^ value2 = { {0, 1}, {2, 3} };  
  
   array<V, 2>^ value3 = gcnew array<V, 2>{ {V(0), V(1)}, {V(2), V(3)} };  
   array<V, 2>^ value4 = { {V(0), V(1)}, {V(2), V(3)} };  
  
   array<N*, 2>^ native1 = gcnew array<N*, 2>{ {new N(0), new N(1)},   
      {new N(2), new N(3)} };  
   array<N*, 2>^ native2 = { {new N(0), new N(1)}, {new N(2), new N(3)} };  
}  
```  
  
## 交错数组  
 本节演示如何创建一维托管数组引用、值和本机指针类型。  它还演示如何从函数返回托管数组的单维数组以及如何传递作为参数的一维数组给函数。  
  
```  
// mcppv2_array_of_arrays.cpp  
// compile with: /clr  
using namespace System;  
  
#define ARRAY_SIZE 2  
  
value struct MyStruct {  
   int m_i;  
};  
  
ref class MyClass {  
public:  
   int m_i;  
};  
  
// Returns an array of managed arrays of a reference type.  
array<array<MyClass^>^>^ Test0() {  
   int size_of_array = 4;  
   array<array<MyClass^>^>^ local = gcnew   
      array<array<MyClass^>^>(ARRAY_SIZE);  
  
   for (int i = 0 ; i < ARRAY_SIZE ; i++, size_of_array += 4) {  
      local[i] = gcnew array<MyClass^>(size_of_array);  
      for (int k = 0; k < size_of_array ; k++) {  
         local[i][k] = gcnew MyClass;  
         local[i][k] -> m_i = i;  
      }  
   }  
  
   return local;  
}  
  
// Returns a managed array of Int32.  
array<array<Int32>^>^ Test1() {  
   int i;  
   array<array<Int32>^>^ local = gcnew array<array< Int32 >^>(ARRAY_SIZE);  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++) {  
      local[i] = gcnew array< Int32 >(ARRAY_SIZE);  
         for ( int j = 0 ; j < ARRAY_SIZE ; j++ )   
            local[i][j] = i + 10;  
   }  
   return local;  
}  
  
int main() {  
   int i, j;  
  
   // Declares an array of user-defined reference types  
   // and uses a function to initialize.  
   array< array< MyClass^ >^ >^ MyClass0;  
   MyClass0 = Test0();  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++)  
      for ( j = 0 ; j < ARRAY_SIZE ; j++ )   
         Console::WriteLine("MyClass0[{0}] = {1}", i, MyClass0[i][j] -> m_i);  
   Console::WriteLine();  
  
   // Declares an array of value types and uses a function to initialize.  
   array< array< Int32 >^ >^ IntArray;  
   IntArray = Test1();  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++)  
      for (j = 0 ; j < ARRAY_SIZE ; j++)  
      Console::WriteLine("IntArray[{0}] = {1}", i, IntArray[i][j]);  
   Console::WriteLine();  
  
   // Declares and initializes an array of user-defined value types.  
   array< MyStruct >^ MyStruct1 = gcnew array< MyStruct >(ARRAY_SIZE);  
   for (i = 0 ; i < ARRAY_SIZE ; i++) {  
      MyStruct1[i] = MyStruct();  
      MyStruct1[i].m_i = i + 40;  
   }  
  
   for (i = 0 ; i < ARRAY_SIZE ; i++)  
      Console::WriteLine(MyStruct1[i].m_i);  
}  
  
```  
  
 **Output**  
  
  **MyClass0\[0\] \= 0**  
**MyClass0\[0\] \= 0**  
**MyClass0\[1\] \= 1**  
**MyClass0\[1\] \= 1**  
**IntArray\[0\] \= 10**  
**IntArray\[0\] \= 10**  
**IntArray\[1\] \= 11**  
**IntArray\[1\] \= 11**  
**40**  
**41** 下面的示例显示如何执行交错数组的聚合初始化。  
  
```  
// mcppv2_array_of_arrays_aggregate_init.cpp  
// compile with: /clr  
using namespace System;  
#define ARRAY_SIZE 2  
int size_of_array = 4;  
int count = 0;  
  
ref class MyClass {  
public:  
   int m_i;  
};  
  
struct MyNativeClass {  
   int m_i;  
};  
  
int main() {  
   // Declares an array of user-defined reference types  
   // and performs an aggregate initialization.  
   array< array< MyClass^ >^ >^ MyClass0 = gcnew array<array<MyClass^>^> {  
      gcnew array<MyClass^>{ gcnew MyClass(), gcnew MyClass() },  
      gcnew array<MyClass^>{ gcnew MyClass(), gcnew MyClass() }  
   };  
  
   for ( int i = 0 ; i < ARRAY_SIZE ; i++, size_of_array += 4 )  
      for ( int k = 0 ; k < ARRAY_SIZE ; k++ )  
         MyClass0[i][k] -> m_i = i;  
  
   for ( int i = 0 ; i < ARRAY_SIZE ; i++ )  
      for ( int j = 0 ; j < ARRAY_SIZE ; j++ )   
         Console::WriteLine("MyClass0[{0}] = {1}", i, MyClass0[i][j] -> m_i);  
   Console::WriteLine();  
  
   // Declares an array of value types and performs an aggregate initialization.  
   array< array< Int32 >^ >^ IntArray = gcnew array<array< Int32 >^> {  
      gcnew array<Int32>{1,2},  
      gcnew array<Int32>{3,4,5}  
   };  
  
   for each ( array<int>^ outer in IntArray ) {  
      Console::Write("[");   
  
      for each( int i in outer )  
         Console::Write(" {0}", i);  
  
      Console::Write(" ]");  
      Console::WriteLine();  
   }  
   Console::WriteLine();  
  
   // Declares and initializes an array of pointers to a native type.  
   array<array< MyNativeClass * >^ > ^ MyClass2 =   
      gcnew array<array< MyNativeClass * > ^> {  
         gcnew array<MyNativeClass *>{ new MyNativeClass(), new MyNativeClass() },  
         gcnew array<MyNativeClass *>{ new MyNativeClass(), new MyNativeClass(), new MyNativeClass() }  
      };  
  
   for each ( array<MyNativeClass *> ^ outer in MyClass2 )  
      for each( MyNativeClass* i in outer )  
         i->m_i = count++;  
  
   for each ( array<MyNativeClass *> ^ outer in MyClass2 ) {  
      Console::Write("[");  
      for each( MyNativeClass* i in outer )  
         Console::Write(" {0}", i->m_i);  
      Console::Write(" ]");  
      Console::WriteLine();  
   }  
   Console::WriteLine();  
  
   // Declares and initializes an array of two-dimensional arrays of strings.  
   array<array<String ^,2> ^> ^gc3 = gcnew array<array<String ^,2> ^>{   
      gcnew array<String ^>{ {"a","b"}, {"c", "d"}, {"e","f"} },  
      gcnew array<String ^>{ {"g", "h"} }   
   };  
  
   for each ( array<String^, 2> ^ outer in gc3 ){  
      Console::Write("[");  
      for each( String ^ i in outer )  
         Console::Write(" {0}", i);  
      Console::Write(" ]");  
      Console::WriteLine();  
   }  
}  
  
```  
  
 **Output**  
  
  **MyClass0\[0\] \= 0**  
**MyClass0\[0\] \= 0**  
**MyClass0\[1\] \= 1**  
**MyClass0\[1\] \= 1**  
**\[ 1 2 \]**  
**\[ 3 4 5 \]**  
**\[ 0 1 \]**  
**\[ 2 3 4 \]**  
**\[ a b c d e f \]**  
**\[ g h \]**   
## 托管数组作为模板类型参数  
 此示例演示如何使用托管数组作为模板的参数：  
  
```  
// mcppv2_template_type_params.cpp  
// compile with: /clr  
using namespace System;  
template <class T>   
class TA {  
public:  
   array<array<T>^>^ f() {  
      array<array<T>^>^ larr = gcnew array<array<T>^>(10);  
      return larr;  
   }  
};  
  
int main() {  
   int retval = 0;  
   TA<array<array<Int32>^>^>* ta1 = new TA<array<array<Int32>^>^>();  
   array<array<array<array<Int32>^>^>^>^ larr = ta1->f();  
   retval += larr->Length - 10;  
   Console::WriteLine("Return Code: {0}", retval);  
}  
  
```  
  
 **Output**  
  
  **返回代码:0**   
## 托管数组的类型定义  
 此示例演示如何使托管数组的类型定义:  
  
```  
// mcppv2_typedef_arrays.cpp  
// compile with: /clr  
using namespace System;  
ref class G {};  
  
typedef array<array<G^>^> jagged_array;  
  
int main() {  
   jagged_array ^ MyArr = gcnew jagged_array (10);  
}  
  
```  
  
## 对数组进行排序  
 与标准 C\+\+ 数组不同，托管数组从继承于常见的行为的基类数组中隐式继承。  示例是 `Sort` 方法，该方法可用于指定所有数组的项。  
  
 对于包含的基本内部类型的数组，可调用 `Sort` 方法。  当要排序某些复杂类型时，可以重写排序标准，也必须重写。  在这种情况下，数组元素类型必须实现[IComparable::CompareTo](https://msdn.microsoft.com/en-us/library/system.icomparable.compareto.aspx)方法。  
  
```  
// array_sort.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   array<int>^ a = { 5, 4, 1, 3, 2 };  
   Array::Sort( a );  
   for (int i=0; i < a->Length; i++)  
      Console::Write("{0} ", a[i] );  
}  
  
```  
  
## 使用自定义条件排序数组  
 若要对包含基本的内部类型的数组排序，可调用 `Array::Sort` 方法。  但是，要对包含复杂类型或重写默认排序条件的数组排序，请重写[IComparable::CompareTo](https://msdn.microsoft.com/en-us/library/system.icomparable.compareto.aspx)方法。  
  
 在下面的示例中，名为 `Element` 的结构从 <xref:System.IComparable>派生，并提供使用计算两个整数作为排序条件的 <xref:System.IComparable.CompareTo%2A> 方法。  
  
```  
using namespace System;  
  
value struct Element : public IComparable {  
   int v1, v2;  
  
   virtual int CompareTo(Object^ obj) {  
      Element^ o = dynamic_cast<Element^>(obj);  
      if (o) {  
         int thisAverage = (v1 + v2) / 2;  
         int thatAverage = (o->v1 + o->v2) / 2;  
         if (thisAverage < thatAverage)  
            return -1;  
         else if (thisAverage > thatAverage)  
            return 1;  
         return 0;  
         }  
      else  
         throw gcnew ArgumentException  
      ("Object must be of type 'Element'");  
   }  
};  
  
int main() {  
   array<Element>^ a = gcnew array<Element>(10);  
   Random^ r = gcnew Random;  
  
   for (int i=0; i < a->Length; i++) {  
      a[i].v1 = r->Next() % 100;  
      a[i].v2 = r->Next() % 100;  
   }  
  
   Array::Sort( a );  
   for (int i=0; i < a->Length; i++) {  
      int v1 = a[i].v1;  
      int v2 = a[i].v2;  
      int v = (v1 + v2) / 2;  
      Console::WriteLine("{0}  (({1}+{2})/2) ", v, v1, v2);  
   }  
}  
```  
  
## 数组协方差  
 具备直接或间接基类 B 的特定引用类 D，数组类型 D 可分配给类型 B 的数组变量。  
  
```  
// clr_array_covariance.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   // String derives from Object.  
   array<Object^>^ oa = gcnew array<String^>(20);  
}  
```  
  
 对数组的元素的分配与数组的动态类型的分配兼容。  不兼容类型的数组元素的分配将导致抛出 `System::ArrayTypeMismatchException`。  
  
 "数组协方差"不适用于某些值类类型的数组。  例如，Int32 数组无法转换为 Object^ 数组，使用装箱技术也不行。  
  
```  
// clr_array_covariance2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct Base { int i; };  
ref struct Derived  : Base {};  
ref struct Derived2 : Base {};  
ref struct Derived3 : Derived {};  
ref struct Other { short s; };  
  
int main() {  
   // Derived* d[] = new Derived*[100];  
   array<Derived^> ^ d = gcnew array<Derived^>(100);  
  
   // ok by array covariance  
   array<Base ^> ^  b = d;  
  
   // invalid  
   // b[0] = new Other;  
  
   // error (runtime exception)  
   // b[1] = gcnew Derived2;  
  
   // error (runtime exception),  
   // must be "at least" a Derived.  
   // b[0] = gcnew Base;  
  
   b[1] = gcnew Derived;  
   b[0] = gcnew Derived3;  
}  
```  
  
## 请参阅  
 [数组](../windows/arrays-cpp-component-extensions.md)