---
title: 重写说明符 （c + + 组件扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- override specifiers, Visual C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4eb610157d1d56c00b48e98086137351e9fd43a8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="override-specifiers--c-component-extensions"></a>重写说明符（C++ 组件扩展）
*重写说明符*修改如何继承的类型和继承类型成员在派生类型中的行为。  
  
## <a name="all-runtimes"></a>所有运行时  
 **备注**  
  
 有关重写说明符的详细信息，请参阅：  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [新 (新 vtable 中的槽）](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
-   [override](../windows/override-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   [重写说明符和本机编译](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)  
  
 `abstract` 和 `sealed` 也对类型声明有效，在类型声明中它们不用作重写说明符。  
  
 有关显式重写基类函数的信息，请参阅[显式重写](../windows/explicit-overrides-cpp-component-extensions.md)。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 (此语言功能没有只适用于 Windows 运行时的备注。）  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时  
 （此语言功能没有只适用于公共运行时的备注。）  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)