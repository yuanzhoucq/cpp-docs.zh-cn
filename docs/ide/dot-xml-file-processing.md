---
title: ".Xml 文件处理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: XML documentation, processing XML file
ms.assetid: e70fdeae-80ac-4872-ab24-771c5635cfbf
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3a1c0ced45fc7f9c4e51a5dbe8a888c030a6b957
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="xml-file-processing"></a>.Xml 文件处理
编译器为代码（已标记以生成文档）中的每个构造生成一个 ID 字符串。 有关详细信息，请参阅[建议标记文档注释](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)。 ID 字符串唯一标识构造。 处理的.xml 文件的程序可使用的 ID 字符串以确定将应用文档的相应.NET Framework 元数据或反射项目。  
  
 .Xml 文件不是你的代码的分层表示形式，它是与每个元素的生成 ID 的平面列表。  
  
 编译器在生成 ID 字符串时应遵循以下规则：  
  
-   在字符串中不放置任何空格。  
  
-   ID 字符串的第一部分标识的标识，与单个字符跟一个冒号的成员的类型。 使用下面的成员类型：  
  
    |字符|描述|  
    |---------------|-----------------|  
    |N|namespace<br /><br /> 无法将文档注释添加到命名空间，可能会出现到命名空间的 cref 引用。|  
    |T|类型：类、接口、结构、枚举、委托|  
    |D|typedef|  
    |F|Field — 字段|  
    |P|属性（包括索引器或其他的索引属性）|  
    |M|方法（包括构造函数、运算符等特殊方法）|  
    |E|Event — 事件|  
    |!|错误字符串<br /><br /> 字符串的其余部分提供有关错误的信息。 Visual c + + 编译器将生成错误无法解析的链接的信息。|  
  
-   该字符串的第二部分是项目的完全限定名称，从命名空间的根开始。 用句点分隔的项、 其封闭类型或类型和命名空间的名称。 如果项目名称本身包含句点，会将其替换为哈希符号 ('#')。 假定任何项直接在其名称中拥有一个哈希符号。 例如，完全限定的名称的`String`构造函数将为"System.String.#ctor"。  
  
-   对于属性和方法，如果方法带有自变量，则后跟用括号括起来的自变量列表。 如果没有任何自变量，则不会出现括号。 确保自变量之间用逗号分隔。 每个自变量的编码直接遵循它在 .NET Framework 签名中的编码方式：  
  
    -   基类型。 常规的类型（ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE）表示为该类型的完全限定名称。  
  
    -   内部类型（例如，ELEMENT_TYPE_I4、ELEMENT_TYPE_OBJECT、ELEMENT_TYPE_STRING、ELEMENT_TYPE_TYPEDBYREF 和 ELEMENT_TYPE_VOID） 例如，表示为相应的完整类型的完全限定名称**System.Int32**或**System.TypedReference**。  
  
    -   ELEMENT_TYPE_PTR 表示为修改类型之后的“*”。  
  
    -   ELEMENT_TYPE_BYREF 表示为修改类型之后的“@”。  
  
    -   ELEMENT_TYPE_PINNED 表示为修改类型之后的“^”。 Visual C++ 编译器绝不生成它。  
  
    -   ELEMENT_TYPE_CMOD_REQ 表示为“&#124;”和修饰符类的完全限定名称，前面是修改类型。 Visual C++ 编译器绝不生成它。  
  
    -   ELEMENT_TYPE_CMOD_OPT 表示为“!”和修饰符类的完全限定名称，前面是修改类型。  
  
    -   ELEMENT_TYPE_SZARRAY 表示为“[]”，前面是数组的元素类型。  
  
    -   ELEMENT_TYPE_GENERICARRAY 表示为“[?]”，前面是数组的元素类型。 Visual C++ 编译器绝不生成它。  
  
    -   ELEMENT_TYPE_ARRAY 表示为 [*lowerbound*:`size`,*lowerbound*:`size`]，其中逗号的数量是秩 - 1，每个维度的下限和大小（如果已知）以十进制形式表示。 如果未指定下限或大小，则只需将其省略。 如果省略某个特定维度的下限和大小，也会省略“:”。 例如，以 1 作为下限并且未指定大小的二维数组是 [1:,1:]。  
  
    -   ELEMENT_TYPE_FNPTR 表示为“=FUNC:`type`(*signature*)”，其中 `type` 是返回类型，*signature* 是方法的自变量。 如果没有任何自变量，则省略括号。 Visual C++ 编译器绝不生成它。  
  
     不表示下列签名组件，因为它们永远不会用于区分重载方法：  
  
    -   调用约定  
  
    -   返回类型  
  
    -   ELEMENT_TYPE_SENTINEL  
  
-   为转换运算符，该方法的返回值被编码为 ~ 跟返回类型，如前面编码。  
  
-   对于泛型类型，类型名称后跟反勾号，然后是指示泛型类型参数数量的一个数字。  例如，  
  
    ```  
    <member name="T:MyClass`2">  
    ```  
  
     类型定义为`public class MyClass<T, U>`。  
  
     对于采用方法都将作为参数的泛型类型，泛型类型参数被指定为数字前面加上反勾 (例如\`0， \`1)。  每个数字表示该类型的泛型参数的从零开始的数组表示法。  
  
## <a name="example"></a>示例  
 下面的示例演示如何的 ID 字符串类并将生成其成员。  
  
```  
// xml_id_strings.cpp  
// compile with: /clr /doc /LD  
///   
namespace N {    
// "N:N"  
  
   /// <see cref="System" />  
   //  <see cref="N:System"/>  
   ref class X {      
   // "T:N.X"  
  
   protected:  
      ///   
      !X(){}     
      // "M:N.X.Finalize", destructor's representation in metadata  
  
   public:  
      ///   
      X() {}     
      // "M:N.X.#ctor"  
  
      ///   
      static X() {}     
      // "M:N.X.#cctor"  
  
      ///   
      X(int i) {}     
      // "M:N.X.#ctor(System.Int32)"  
  
      ///   
      ~X() {}     
      // "M:N.X.Dispose", Dispose function representation in metadata  
  
      ///   
      System::String^ q;     
      // "F:N.X.q"  
  
      ///   
      double PI;     
      // "F:N.X.PI"  
  
      ///   
      int f() { return 1; }     
      // "M:N.X.f"  
  
      ///   
      int bb(System::String ^ s, int % y, void * z) { return 1; }  
      // "M:N.X.bb(System.String,System.Int32@,System.Void*)"  
  
      ///   
      int gg(array<short> ^ array1, array< int, 2 >^ IntArray) { return 0; }   
      // "M:N.X.gg(System.Int16[], System.Int32[0:,0:])"  
  
      ///   
      static X^ operator+(X^ x, X^ xx) { return x; }  
     // "M:N.X.op_Addition(N.X,N.X)"  
  
      ///   
      property int prop;     
      // "M:N.X.prop"  
  
      ///   
      property int prop2 {     
      // "P:N.X.prop2"  
  
         ///   
         int get() { return 0; }  
         // M:N.X.get_prop2  
  
         ///   
         void set(int i) {}  
         // M:N.X.set_prop2(System.Int32)  
      }  
  
      ///   
      delegate void D(int i);   
      // "T:N.X.D"  
  
      ///   
      event D ^ d;   
      // "E:N.X.d"  
  
      ///   
      ref class Nested {};   
      // "T:N.X.Nested"  
  
      ///   
      static explicit operator System::Int32 (X x) { return 1; }   
      // "M:N.X.op_Explicit(N.X!System.Runtime.CompilerServices.IsByValue)~System.Int32"  
   };  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)