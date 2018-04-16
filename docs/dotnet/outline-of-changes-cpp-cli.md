---
title: "更改概要 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c0bbbd6b-c5c4-44cf-a6ca-c1010c377e9d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fdc0015bda5f0a6678b1d274c79445aba4e4aab0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="outline-of-changes-ccli"></a>更改概要 (C++/CLI)
此大纲显示你的一些示例的某些更改托管扩展中的语言为 c + + 实现 Visual c + +。 访问附带有关详细信息的每个项的链接。  
  
## <a name="no-double-underscore-keywords"></a>没有双下划线关键字  
 所有关键字的前面的双下划线已删除，但有一个例外。 因此，`__value`变得`value`，和`__interface`变得`interface`，依次类推。 若要防止用户代码中的标识符和关键字之间的名称不冲突，关键字的主要处理上下文。  
  
 请参阅[语言关键字 (C + + /cli CLI)](../dotnet/language-keywords-cpp-cli.md)有关详细信息。  
  
## <a name="class-declarations"></a>类声明  
 托管的扩展语法：  
  
```  
__gc class Block {};                           // reference class  
__value class Vector {};                       // value class  
__interface I {};                        // interface class  
__gc __abstract class Shape {};                // abstract class  
__gc __sealed class Shape2D : public Shape {}; // derived class  
```  
  
 新的语法：  
  
```  
ref class Block {};                // reference class  
value class Vector {};             // value class  
interface class I {};        // interface class  
ref class Shape abstract {};       // abstract class  
ref class Shape2D sealed: Shape{}; // derived class  
```  
  
 请参阅[托管类型 (C + + /cli CL)](../dotnet/managed-types-cpp-cl.md)有关详细信息。  
  
## <a name="object-declaration"></a>对象声明  
 托管的扩展语法：  
  
```  
public __gc class Form1 : public System::Windows::Forms::Form {  
private:  
   System::ComponentModel::Container __gc *components;  
   System::Windows::Forms::Button   __gc *button1;  
   System::Windows::Forms::DataGrid __gc *myDataGrid;     
   System::Data::DataSet  __gc *myDataSet;  
};  
```  
  
 新的语法：  
  
```  
public ref class Form1 : System::Windows::Forms::Form {  
   System::ComponentModel::Container^ components;  
   System::Windows::Forms::Button^ button1;  
   System::Windows::Forms::DataGrid^ myDataGrid;  
   System::Data::DataSet^ myDataSet;  
};  
```  
  
 请参阅[CLR 引用类对象的声明](../dotnet/declaration-of-a-clr-reference-class-object.md)有关详细信息。  
  
### <a name="managed-heap-allocation"></a>托管的堆分配  
 托管的扩展语法：  
  
```  
Button* button1 = new Button; // managed heap  
int *pi1 = new int;           // native heap  
Int32 *pi2 = new Int32;       // managed heap  
```  
  
 新的语法：  
  
```  
Button^ button1 = gcnew Button;        // managed heap  
int * pi1 = new int;                   // native heap  
Int32^ pi2 = gcnew Int32;              // managed heap  
```  
  
 请参阅[CLR 引用类对象的声明](../dotnet/declaration-of-a-clr-reference-class-object.md)有关详细信息。  
  
### <a name="a-tracking-reference-to-no-object"></a>对没有任何对象的跟踪引用  
 托管的扩展语法：  
  
```  
// OK: we set obj to refer to no object  
Object * obj = 0;  
  
// Error: no implicit boxing  
Object * obj2 = 1;  
```  
  
 新的语法：  
  
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
  
 请参阅[CLR 引用类对象的声明](../dotnet/declaration-of-a-clr-reference-class-object.md)有关详细信息。  
  
## <a name="array-declaration"></a>数组声明  
 CLR 数组已经过重新设计。 它是类似于 stl`vector`模板集合，但映射到基础`System::Array`类-即，它不是模板实现。  
  
 请参阅[CLR 数组的声明](../dotnet/declaration-of-a-clr-array.md)有关详细信息。  
  
### <a name="array-as-parameter"></a>作为参数的数组  
 托管的扩展数组语法：  
  
```  
void PrintValues( Object* myArr __gc[]);   
void PrintValues( int myArr __gc[,,]);   
```  
  
 新数组语法：  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
### <a name="array-as-return-type"></a>用作返回类型的数组  
 托管的扩展数组语法：  
  
```  
Int32 f() [];   
int GetArray() __gc[];  
```  
  
 新数组语法：  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
### <a name="shorthand-initialization-of-local-clr-array"></a>速记初始化本地 CLR 数组，数组  
 托管的扩展数组语法：  
  
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
  
### <a name="explicit-clr-array-declaration"></a>显式 CLR 数组声明  
 托管的扩展数组语法：  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 新数组语法：  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 语言： 遵循 gcnew 的显式数组初始化  
  
```  
// explicit initialization list follow gcnew   
// is not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## <a name="scalar-properties"></a>标量属性  
 托管的扩展属性语法：  
  
```  
public __gc __sealed class Vector {  
   double _x;  
  
public:  
   __property double get_x(){ return _x; }  
   __property void set_x( double newx ){ _x = newx; }  
};  
```  
  
 新的属性语法：  
  
```  
public ref class Vector sealed {   
   double _x;  
  
public:  
   property double x   
   {  
      double get()             { return _x; }  
      void   set( double newx ){ _x = newx; }  
   } // Note: no semi-colon  
};  
```  
  
 语言： 普通属性  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   // backing store is not accessible  
   property double x;   
};  
```  
  
 请参阅[属性声明](../dotnet/property-declaration.md)有关详细信息。  
  
## <a name="indexed-properties"></a>索引属性  
 托管的扩展编入索引的属性语法：  
  
```  
public __gc class Matrix {  
   float mat[,];  
  
public:   
   __property void set_Item( int r, int c, float value) { mat[r,c] = value; }  
   __property int get_Item( int r, int c ) { return mat[r,c]; }  
};  
```  
  
 新的索引的属性语法：  
  
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
  
 语言： 类级索引的属性  
  
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
  
 请参阅[属性索引声明](../dotnet/property-index-declaration.md)有关详细信息。  
  
## <a name="overloaded-operators"></a>重载运算符  
 托管的扩展运算符重载语法：  
  
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
  
 请参阅[重载运算符](../dotnet/overloaded-operators.md)有关详细信息。  
  
## <a name="conversion-operators"></a>转换运算符  
 托管的扩展转换运算符语法：  
  
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
  
 请参阅[更改为转换运算符](../dotnet/changes-to-conversion-operators.md)有关详细信息。  
  
## <a name="explicit-override-of-an-interface-member"></a>接口成员的显式重写  
 托管的扩展显式重写语法：  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 新的显式重写语法：  
  
```  
public ref class R : public ICloneable {  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R   
   virtual R^ Clone();  
};  
```  
  
 请参阅[接口成员的显式重写](../dotnet/explicit-override-of-an-interface-member.md)有关详细信息。  
  
## <a name="private-virtual-functions"></a>私有虚函数  
 托管的扩展私有虚函数语法：  
  
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
  
 新的私有虚函数语法  
  
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
  
 请参阅[私有虚拟函数](../dotnet/private-virtual-functions.md)有关详细信息。  
  
## <a name="clr-enum-type"></a>CLR 枚举类型  
 托管的扩展枚举语法：  
  
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
  
 除了此小语法更改后，CLR 枚举类型的行为已更改多种方式：  
  
-   不再支持的 CLR 枚举的前向声明。  
  
-   内置算术类型的对象类层次结构之间的重载解决方案中托管扩展和 Visual c + + 之间相反。 作为其副作用是，CLR 枚举将不再隐式转换为算术类型。  
  
-   在新语法中，CLR 枚举维护自己的作用域，不是这种情况在托管扩展。 以前，枚举器是在枚举，则包含作用域内可见现在，枚举器枚举的作用域内封装。  
  
 请参阅[CLR 枚举类型](../dotnet/clr-enum-type.md)有关详细信息。  
  
## <a name="removal-of-box-keyword"></a>__Box 关键字中删除  
 装箱语法的托管的扩展：  
  
```  
Object *o = __box( 1024 ); // explicit boxing  
```  
  
 新的装箱语法：  
  
```  
Object ^o = 1024; // implicit boxing  
```  
  
 请参阅[装箱值的跟踪句柄](../dotnet/a-tracking-handle-to-a-boxed-value.md)有关详细信息。  
  
## <a name="pinning-pointer"></a>钉住指针  
 钉住指针语法的托管的扩展：  
  
```  
__gc struct H { int j; };  
  
int main() {  
   H * h = new H;  
   int __pin * k = & h -> j;  
};  
```  
  
 新钉住指针语法：  
  
```  
ref struct H { int j; };  
  
int main() {  
   H^ h = gcnew H;  
   pin_ptr<int> k = &h->j;  
}  
```  
  
 请参阅[值类型语义](../dotnet/value-type-semantics.md)有关详细信息。  
  
## <a name="typeof-keyword-becomes-typeid"></a>__typeof 关键字将成为 typeid  
 托管的扩展 typeof 语法：  
  
```  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 新的 typeid 语法：  
  
```  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
 请参阅[typeof 转到 t:: typeid](../dotnet/typeof-goes-to-t-typeid.md)有关详细信息。  
  
## <a name="see-also"></a>请参阅  
 [C + + /cli 迁移入门](../dotnet/cpp-cli-migration-primer.md)   
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)


