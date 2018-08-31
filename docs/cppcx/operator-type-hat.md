---
title: 运算符 Type ^ |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8530a3c896d5c1dfa6568e166b9a0a43c0f0b0fc
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208082"
---
# <a name="operator-type"></a>运算符 Type^
启用从转换[Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)到`Platform::Type`。  
  
## <a name="syntax"></a>语法  
  
```cpp  
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName)  
```  
  
### <a name="return-value"></a>返回值  
 返回`Platform::Type`在给定[Windows::UI::Xaml::Interop::TypeName](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)。  
  
### <a name="remarks"></a>备注  
 `TypeName` 是表示类型信息的中性语言 Windows 运行时结构。 [Platform::Type](../cppcx/platform-type-class.md) 特定于 C++，无法通过应用程序二进制接口 (ABI) 传递。 下面是一个利用`TypeName`，请在[Navigate](https://msdn.microsoft.com/library/windows/apps/hh702394.aspx)函数：  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
### <a name="example"></a>示例  
 下一示例演示如何在 `TypeName` 和 `Type`之间转换。  
  
```  
  
// Convert from Type to TypeName  
TypeName tn = TypeName(MainPage::typeid);  
  
// Convert back from TypeName to Type  
Type^ tx2 = (Type^)(tn);  
  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 .NET Framework 程序将 `TypeName` 投影为 [System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True)的转换。  
  
### <a name="requirements"></a>要求  
  
## <a name="see-also"></a>请参阅  
 [运算符 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)   
 [Platform::Type 类](../cppcx/platform-type-class.md)