---
title: 与 clr 的 C 样式强制转换 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 384aa6d1d7a4329f52157f1d002dcda2feb5cb8a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860393"
---
# <a name="c-style-casts-with-clr-ccli"></a>C 风格的强制转换和 /clr (C++/CLI)
以下主题仅适用于公共语言运行时。  
  
 当与 CLR 类型一起使用，编译器将尝试映射 C 样式强制转换为一个强制转换下列，按以下顺序：  
  
1.  const_cast  
  
2.  safe_cast  
  
3.  safe_cast 加上 const_cast  
  
4.  static_cast  
  
5.  static_cast 加上 const_cast  
  
 如果强制转换上面列出的所有均有效，以及如果表达式的类型和目标类型是 CLR 引用类型，C 样式强制转换将映射到运行时检查 （castclass MSIL 指令）。 否则为 C 样式强制转换将被视为无效，编译器会发出错误。  
  
## <a name="remarks"></a>备注  
 不建议 C 样式强制转换。 使用编译时[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)，使用[safe_cast](../windows/safe-cast-cpp-component-extensions.md)。  
  
 下面的示例演示 C 样式强制转换映射到`const_cast`。  
  
```  
// cstyle_casts_1.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
int main() {  
   const R^ constrefR = gcnew R();  
   R^ nonconstR = (R^)(constrefR);   
}  
```  
  
 下面的示例演示 C 样式强制转换映射到`safe_cast`。  
  
```  
// cstyle_casts_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Object ^ o = "hello";  
   String ^ s = (String^)o;  
}  
```  
  
 下面的示例演示 C 样式强制转换映射到`safe_cast`加上`const_cast`。  
  
```  
// cstyle_casts_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
ref struct R2 : public R {};  
  
int main() {  
   const R^ constR2 = gcnew R2();  
   try {  
   R2^ b2DR = (R2^)(constR2);  
   }  
   catch(InvalidCastException^ e) {  
      System::Console::WriteLine("Invalid Exception");  
   }  
}  
```  
  
 下面的示例演示 C 样式强制转换映射到`static_cast`。  
  
```  
// cstyle_casts_4.cpp  
// compile with: /clr  
using namespace System;  
  
struct N1 {};  
struct N2 {  
   operator N1() {  
      return N1();  
   }  
};  
  
int main() {  
   N2 n2;  
   N1 n1 ;  
   n1 = (N1)n2;  
}  
```  
  
 下面的示例演示 C 样式强制转换映射到`static_cast`加上`const_cast`。  
  
```  
// cstyle_casts_5.cpp  
// compile with: /clr  
using namespace System;  
struct N1 {};  
  
struct N2 {  
   operator const N1*() {  
      static const N1 n1;  
      return &n1;  
   }  
};  
  
int main() {  
   N2 n2;  
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast  
}  
```  
  
 下面的示例演示 C 样式强制转换映射到运行时检查。  
  
```  
// cstyle_casts_6.cpp  
// compile with: /clr  
using namespace System;  
  
ref class R1 {};  
ref class R2 {};  
  
int main() {  
   R1^ r  = gcnew R1();  
   try {  
      R2^ rr = ( R2^)(r);  
   }  
   catch(System::InvalidCastException^ e) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 下面的示例显示无效 C 样式强制转换，这将导致编译器发出错误。  
  
```  
// cstyle_casts_7.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String^s = S"hello";  
   int i = (int)s;   // C2440  
}  
```  
  
## <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)