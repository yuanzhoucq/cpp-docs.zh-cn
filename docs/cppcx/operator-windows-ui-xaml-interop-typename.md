---
title: 运算符 Windows::UI::Xaml::Interop::TypeName |Microsoft 文档
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 714d39a70b19998a5daddceadc2c91df65312122
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="operator-windowsuixamlinteroptypename"></a>运算符 Windows::UI::Xaml::Interop::TypeName
实现从 `Platform::Type` 到 [Windows::UI::Xaml::Interop::TypeName](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx)的转换。  
  
## <a name="syntax"></a>语法  
  
```cpp  
Operator TypeName(Platform::Type^ type)  
```  
  
### <a name="return-value"></a>返回值  
 给定 [时返回](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.interop.typename.aspx) Windows::UI::Xaml::Interop::TypeName `Platform::Type^`。  
  
### <a name="remarks"></a>备注  
 `TypeName` 是表示类型信息的中性语言 Windows 运行时结构。 [Platform::Type](../cppcx/platform-type-class.md) 特定于 C++，无法通过应用程序二进制接口 (ABI) 传递。 下面是 `TypeName`在 [Navigate](http://msdn.microsoft.com/library/windows/apps/hh702394.aspx) 函数中的一种用法：  
  
```  
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);  
```  
  
### <a name="example"></a>示例  
 下一示例演示如何在 `TypeName` 和 `Type`之间转换。  
  
```  
  
// Convert from Type to TypeName  
Windows::UI::Xaml::Interop::TypeName tn = TypeName(MainPage::typeid);  
  
// Convert back from TypeName to Type  
Type^ tx2 = (Type^)(tn);  
  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 .NET Framework 程序将 `TypeName` 投影为 [System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True)的转换。  
  
### <a name="requirements"></a>要求  
  
## <a name="see-also"></a>请参阅  
 [运算符 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)   
 [Platform::Type 类](../cppcx/platform-type-class.md)