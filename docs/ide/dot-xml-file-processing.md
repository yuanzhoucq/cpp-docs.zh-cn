---
title: ".Xml 文件处理 | Microsoft Docs"
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
  - "XML 文档, 处理 XML 文件"
ms.assetid: e70fdeae-80ac-4872-ab24-771c5635cfbf
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# .Xml 文件处理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

编译器为代码中被标记为生成文档的每一个构造生成一个 ID 字符串。  有关更多信息，请参见 [建议的标记文档注释](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)。  ID 字符串唯一地标识构造。  处理 .xml 文件的程序可以使用 ID 字符串标识文档应用相应的 .NET framework 元数据或反射项目。  
  
 .xml 文件不是代码，它的分层表示形式是简单列表中的每个元素生成的 ID。  
  
 编译器在生成 ID 字符串时遵循下列规则：  
  
-   不在字符串中放置空白。  
  
-   ID 字符串的第一部分通过单个字符后跟一个冒号来标识被标识成员的种类。  使用下列成员类型：  
  
    |字符|描述|  
    |--------|--------|  
    |N|命名空间<br /><br /> 不能将文档注释到命名空间，cref 对命名空间是可能的。|  
    |T|类型：类、接口、结构、枚举、委托|  
    |D|typedef|  
    |F|字段|  
    |P|属性（包括索引程序或其他索引属性）|  
    |M|方法（包括一些特殊方法，例如构造函数、运算符等）|  
    |E|事件|  
    |\!|错误字符串<br /><br /> 字符串的其余部分会提供有关此错误的信息。  Visual C\+\+ 编译器生成未能解析的链接的错误信息。|  
  
-   字符串的第二部分是项的完全限定名，从命名空间的根开始。  该项目的名称，其封闭类型或类型和命名空间在句点分隔。  如果项的名称本身包含句号，则用哈希符号 \('\#'\) 替换这些句号。  假定，项目没有一个哈希符号直接在其名称。  例如，`String` 构造函数的完全限定名称为“System.String.\#ctor”。  
  
-   对于属性和方法，如果该方法带参数，则将其后的参数列表括在括号中。  如果没有参数，则没有括号。  多个参数以逗号分隔。  每个参数的编码都直接遵循它在 .NET Framework 签名中的编码方法：  
  
    -   基类型。  常规类型（ELEMENT\_TYPE\_CLASS 或 ELEMENT\_TYPE\_VALUETYPE）表示为类型的完全限定名。  
  
    -   内部类型（例如，ELEMENT\_TYPE\_I4、ELEMENT\_TYPE\_OBJECT、ELEMENT\_TYPE\_STRING、ELEMENT\_TYPE\_TYPEDBYREF。  并 ELEMENT\_TYPE\_VOID\) 表示为相应的完整类型，例如，**System.Int32** 或 **System.TypedReference**的完全限定名。  
  
    -   ELEMENT\_TYPE\_PTR 表示为“\*”，在修改的类型之后。  
  
    -   ELEMENT\_TYPE\_BYREF 表示为“@”，在修改的类型之后。  
  
    -   ELEMENT\_TYPE\_PINNED 表示为“^”，在修改的类型之后。  Visual C\+\+ 编译器不生成此操作。  
  
    -   ELEMENT\_TYPE\_CMOD\_REQ 表示为“&#124;”和修饰符类的完全限定名，在修改的类型之后。  Visual C\+\+ 编译器不生成此操作。  
  
    -   ELEMENT\_TYPE\_CMOD\_OPT 表示为“\!”和修饰符类的完全限定名，在修改的类型之后。  
  
    -   ELEMENT\_TYPE\_SZARRAY 表示为“\[\]”，在数组的元素类型之后。  
  
    -   ELEMENT\_TYPE\_GENERICARRAY 表示为“\[?\]”，在数组的元素类型之后。  Visual C\+\+ 编译器不生成此操作。  
  
    -   ELEMENT\_TYPE\_ARRAY 表示为 \[*lowerbound*:`size`,*lowerbound*:`size`\]，其中逗号数为秩 \- 1，每一维的下限和大小（如果已知）用十进制表示。  如果未指定下限及大小，它将完全被省略。  如果省略了特定维的下限及大小，则“:”也将被省略。  例如，以 1 作为下限并且未指定大小的二维数组是 \[1:,1:\]。  
  
    -   ELEMENT\_TYPE\_FNPTR 表示为“\=FUNC:`type`\(*signature*\)”，其中 `type` 是返回类型，*signature* 是方法的参数。  如果没有参数，则将省略括号。  Visual C\+\+ 编译器不生成此操作。  
  
     不表示下列签名组件，因为从不使用它们来区分重载方法：  
  
    -   调用约定  
  
    -   返回类型  
  
    -   ELEMENT\_TYPE\_SENTINEL  
  
-   仅对于转换运算符，方法的返回值按“&#124;”的返回类型添加，如先前输入。  
  
-   对于泛型类型，类型名称后跟反勾号，再跟一个数字，指示泛型类型参数的个数。  例如，  
  
    ```  
    <member name="T:MyClass`2">  
    ```  
  
     为定义为 `public class MyClass<T, U>`的类型。  
  
     对于接受泛型类型作为参数的方法，泛型类型参数被指定为数字前面加上反勾号（如 \`0、\`1）。  表示类型泛型参数的数组表示法（从零开始）的每个数字。  
  
## 示例  
 下面的示例演示选件类的 ID 字符串及其成员如何将生成。  
  
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
  
## 请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)