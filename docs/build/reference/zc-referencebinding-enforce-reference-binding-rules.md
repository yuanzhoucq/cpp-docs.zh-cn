---
title: "/Zc:referenceBinding （强制实施引用绑定规则） |Microsoft 文档"
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0d3d352394b61f95e083a2e6e6f0d888fe210b37
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc:referenceBinding （强制实施引用绑定规则）
当**/Zc:referenceBinding**指定选项，编译器不允许将绑定到一个临时的非常量左值引用。  
  
## <a name="syntax"></a>语法  
  
```  
/Zc:referenceBinding[-]  
```  
  
## <a name="remarks"></a>备注  
如果**/Zc:referenceBinding**指定，则编译器遵循 C + + 11 标准 8.5.3 部分，并且不允许将临时的用户定义的类型绑定到非 const 左值引用的表达式。 默认情况下，或者如果**/Zc:referenceBinding-**指定，编译器允许此类表达式作为 Microsoft 扩展，但发布的 4 级警告。 对于代码安全性、 可移植性和一致性，我们建议你使用**/Zc:referenceBinding**。 [/ 宽松-](permissive-standards-conformance.md)编译器选项隐式设置此选项，但它可以通过重写**/Zc:referenceBinding-**。  
  
## <a name="example"></a>示例  
  
此示例演示 Microsoft 扩展，它允许用户定义类型的一个临时绑定到非 const 左值引用。
```cpp  
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

void main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```  
  
有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +**文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  修改**其他选项**属性以包含**/Zc:referenceBinding** ，然后选择**确定**。  
  
## <a name="see-also"></a>请参阅  
[编译器选项](../../build/reference/compiler-options.md)   
[设置编译器选项](../../build/reference/setting-compiler-options.md)   
[/Zc （一致性）](../../build/reference/zc-conformance.md)