---
title: "更改概要 (C++/CLI) | Microsoft Docs"
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
ms.assetid: c0bbbd6b-c5c4-44cf-a6ca-c1010c377e9d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 更改概要 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此概要给出一些示例，说明 C\+\+ 托管扩展与 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 语言的某些不同。  有关更多信息，请访问每个项附带的链接。  
  
## 没有双下划线的关键字  
 移除了所有关键字前面的双下划线，仅有一个例外。  这样，`__value` 变为 `value`，而 `__interface` 变为 `interface` 等等。  若要防止用户代码中关键字与标识符之间的冲突，请首先将关键字视为上下文。  
  
 有关更多信息，请参见[语言关键字 \(C\+\+\/CLI\)](../dotnet/language-keywords-cpp-cli.md)。  
  
## 类声明  
 托管扩展语法：  
  
```  
__gc class Block {};                           // reference class  
__value class Vector {};                       // value class  
__interface I {};                        // interface class  
__gc __abstract class Shape {};                // abstract class  
__gc __sealed class Shape2D : public Shape {}; // derived class  
```  
  
 新语法：  
  
```  
ref class Block {};                // reference class  
value class Vector {};             // value class  
interface class I {};        // interface class  
ref class Shape abstract {};       // abstract class  
ref class Shape2D sealed: Shape{}; // derived class  
```  
  
 有关更多信息，请参见[托管类型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)。  
  
## 对象声明  
 托管扩展语法：  
  
```  
public __gc class Form1 : public System::Windows::Forms::Form {  
private:  
   System::ComponentModel::Container __gc *components;  
   System::Windows::Forms::Button   __gc *button1;  
   System::Windows::Forms::DataGrid __gc *myDataGrid;     
   System::Data::DataSet  __gc *myDataSet;  
};  
```  
  
 新语法：  
  
```  
public ref class Form1 : System::Windows::Forms::Form {  
   System::ComponentModel::Container^ components;  
   System::Windows::Forms::Button^ button1;  
   System::Windows::Forms::DataGrid^ myDataGrid;  
   System::Data::DataSet^ myDataSet;  
};  
```  
  
 有关更多信息，请参见[CLR 引用类对象的声明](../dotnet/declaration-of-a-clr-reference-class-object.md)。  
  
### 托管堆分配  
 托管扩展语法：  
  
```  
Button* button1 = new Button; // managed heap  
int *pi1 = new int;           // native heap  
Int32 *pi2 = new Int32;       // managed heap  
```  
  
 新语法：  
  
```  
Button^ button1 = gcnew Button;        // managed heap  
int * pi1 = new int;                   // native heap  
Int32^ pi2 = gcnew Int32;              // managed heap  
```  
  
 有关更多信息，请参见[CLR 引用类对象的声明](../dotnet/declaration-of-a-clr-reference-class-object.md)。  
  
### 对不存在的对象的跟踪引用  
 托管扩展语法：  
  
```  
// OK: we set obj to refer to no object  
Object * obj = 0;  
  
// Error: no implicit boxing  
Object * obj2 = 1;  
```  
  
 新语法：  
  
```  
// Incorrect Translation  
// causes the implicit boxing of both 0 and 1  
Object ^ obj = 0;  
Object ^ obj2 = 1;  
  
// Correct Translation  
// OK: we set obj to refer to no object  
Object ^ obj = nullptr;  
  
// OK: we initialize obj2 to an Int32^  
Object ^ obj2 = 1;  
```  
  
 有关更多信息，请参见[CLR 引用类对象的声明](../dotnet/declaration-of-a-clr-reference-class-object.md)。  
  
## 数组声明  
 CLR 数组经过了重新设计。  它类似于 stl `vector` 模板集合，但映射到基础 `System::Array` 类 — 也就是说，它不是模板实现。  
  
 有关更多信息，请参见[CLR 数组的声明](../dotnet/declaration-of-a-clr-array.md)。  
  
### 数组作为参数  
 托管扩展数组语法：  
  
```  
void PrintValues( Object* myArr __gc[]);   
void PrintValues( int myArr __gc[,,]);   
```  
  
 新数组语法：  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
### 数组作为返回类型  
 托管扩展数组语法：  
  
```  
Int32 f() [];   
int GetArray() __gc[];  
```  
  
 新数组语法：  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
### 局部 CLR 数组的简略初始化  
 托管扩展数组语法：  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = { __box(26), __box(27), __box(28),  
                                 __box(29), __box(30) };  
  
   return a1;  
}  
```  
  
 新数组语法：  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
  
   return a1;  
}  
```  
  
### 显式 CLR 数组声明  
 托管扩展数组语法：  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 新数组语法：  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 语言的新功能：显式数组初始化遵循 gcnew  
  
```  
// explicit initialization list follow gcnew   
// is not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## 标量属性  
 托管扩展属性语法：  
  
```  
public __gc __sealed class Vector {  
   double _x;  
  
public:  
   __property double get_x(){ return _x; }  
   __property void set_x( double newx ){ _x = newx; }  
};  
```  
  
 新属性语法：  
  
```  
public ref class Vector sealed {   
   double _x;  
  
public:  
   property double x   
   {  
      double get()             { return _x; }  
      void   set( double newx ){ _x = newx; }  
   } // Note: no semi-colon …  
};  
```  
  
 语言的新功能：trivial 属性  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   // backing store is not accessible  
   property double x;   
};  
```  
  
 有关更多信息，请参见[属性声明](../dotnet/property-declaration.md)。  
  
## 索引属性  
 托管扩展索引属性语法：  
  
```  
public __gc class Matrix {  
   float mat[,];  
  
public:   
   __property void set_Item( int r, int c, float value) { mat[r,c] = value; }  
   __property int get_Item( int r, int c ) { return mat[r,c]; }  
};  
```  
  
 新索引属性语法：  
  
```  
public ref class Matrix {  
   array<float, 2>^ mat;  
  
public:  
   property float Item [int,int] {  
      float get( int r, int c ) { return mat[r,c]; }  
      void set( int r, int c, float value ) { mat[r,c] = value; }  
   }  
};  
```  
  
 语言的新功能：类级索引属性  
  
```  
public ref class Matrix {  
   array<float, 2>^ mat;  
  
public:  
   // ok: class level indexer now  
   //     Matrix mat;  
   //     mat[ 0, 0 ] = 1;   
   //  
   // invokes the set accessor of the default indexer  
  
   property float default [int,int] {  
      float get( int r, int c ) { return mat[r,c]; }  
      void set( int r, int c, float value ) { mat[r,c] = value; }  
   }  
};  
```  
  
 有关更多信息，请参见[属性索引声明](../dotnet/property-index-declaration.md)。  
  
## 重载运算符  
 托管扩展运算符重载语法：  
  
```  
public __gc __sealed class Vector {  
public:  
   Vector( double x, double y, double z );  
  
   static bool    op_Equality( const Vector*, const Vector* );  
   static Vector* op_Division( const Vector*, double );  
};  
  
int main() {  
   Vector *pa = new Vector( 0.231, 2.4745, 0.023 );  
   Vector *pb = new Vector( 1.475, 4.8916, -1.23 );   
  
   Vector *pc = Vector::op_Division( pa, 4.8916 );  
  
   if ( Vector::op_Equality( pa, pc ))  
      ;  
}  
```  
  
 新运算符重载语法：  
  
```  
public ref class Vector sealed {  
public:  
   Vector( double x, double y, double z );  
  
   static bool    operator ==( const Vector^, const Vector^ );  
   static Vector^ operator /( const Vector^, double );  
};  
  
int main() {  
   Vector^ pa = gcnew Vector( 0.231, 2.4745, 0.023 );  
   Vector^ pb = gcnew Vector( 1.475, 4.8916, -1.23 );  
  
   Vector^ pc = pa / 4.8916;  
   if ( pc == pa )  
      ;  
}  
```  
  
 有关更多信息，请参见[重载运算符](../dotnet/overloaded-operators.md)。  
  
## 转换运算符  
 托管扩展转换运算符语法：  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 新转换运算符语法：  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 有关更多信息，请参见[转换运算符的更改](../dotnet/changes-to-conversion-operators.md)。  
  
## 接口成员的显式重写  
 托管扩展显式重写语法：  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 新显式重写语法：  
  
```  
public ref class R : public ICloneable {  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R   
   virtual R^ Clone();  
};  
```  
  
 有关更多信息，请参见[接口成员的显式重写](../dotnet/explicit-override-of-an-interface-member.md)。  
  
## 私有虚函数  
 托管扩展私有虚函数语法：  
  
```  
__gc class Base {  
private:  
   // inaccessible to a derived class  
   virtual void g();   
};  
  
__gc class Derived : public Base {  
public:  
   // ok: g() overrides Base::g()  
   virtual void g();  
};  
```  
  
 新私有虚函数语法  
  
```  
ref class Base {  
private:  
   // inaccessible to a derived class  
   virtual void g();   
};  
  
ref class Derived : public Base {  
public:  
   // error: cannot override: Base::g() is inaccessible  
   virtual void g() override;  
};  
```  
  
 有关更多信息，请参见[私有虚函数](../dotnet/private-virtual-functions.md)。  
  
## CLR 枚举类型  
 托管扩展枚举语法：  
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};    
```  
  
 新枚举语法：  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 除此语法的稍微更改外，CLR 枚举的行为在许多方面发生了更改：  
  
-   不再支持 CLR 枚举的前向声明。  
  
-   内置算术类型和对象类层次结构之间的重载决策在托管扩展和 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之间是相反的。  它的副作用是 CLR 枚举不再隐式转换为算术类型。  
  
-   在新的语法中，CLR 枚举保持其自身范围，而在托管扩展中则不是这样。  以前，枚举数在枚举的包含范围内可见；现在，枚举数被封装在枚举的范围内。  
  
 有关更多信息，请参见[CLR 枚举类型](../dotnet/clr-enum-type.md)。  
  
## 移除 \_\_box 关键字  
 托管扩展装箱语法：  
  
```  
Object *o = __box( 1024 ); // explicit boxing  
```  
  
 新装箱语法：  
  
```  
Object ^o = 1024; // implicit boxing  
```  
  
 有关更多信息，请参见[装箱值的跟踪句柄](../dotnet/a-tracking-handle-to-a-boxed-value.md)。  
  
## 钉住指针  
 托管扩展钉住指针语法：  
  
```  
__gc struct H { int j; };  
  
int main() {  
   H * h = new H;  
   int __pin * k = & h -> j;  
};  
```  
  
 新的钉住指针语法：  
  
```  
ref struct H { int j; };  
  
int main() {  
   H^ h = gcnew H;  
   pin_ptr<int> k = &h->j;  
}  
```  
  
 有关更多信息，请参见[值类型语义](../dotnet/value-type-semantics.md)。  
  
## \_\_typeof 关键字变为 typeid  
 托管扩展 typeof 语法：  
  
```  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 新 typeid 语法：  
  
```  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
 有关更多信息，请参见[typeof 转到 T::typeid](../dotnet/typeof-goes-to-t-typeid.md)。  
  
## 请参阅  
 [C\+\+\/CLI 迁移入门](../dotnet/cpp-cli-migration-primer.md)   
 [\(NOTINBUILD\)Managed Extensions for C\+\+ Syntax Upgrade Checklist](http://msdn.microsoft.com/zh-cn/edbded88-7ef3-4757-bd9d-b8f48ac2aada)   
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)