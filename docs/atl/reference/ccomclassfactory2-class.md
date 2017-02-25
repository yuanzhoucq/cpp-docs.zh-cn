---
title: "CComClassFactory2 Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComClassFactory2<license>"
  - "CComClassFactory2"
  - "ATL.CComClassFactory2<license>"
  - "ATL::CComClassFactory2"
  - "ATL.CComClassFactory2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComClassFactory2 class"
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CComClassFactory2 Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现 [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) 接口。  
  
## 语法  
  
```  
  
      template <  
   class license  
>  
class CComClassFactory2 : public IClassFactory2,  
   public CComObjectRootEx<CComGlobalsThreadModel>,  
   public license  
```  
  
#### 参数  
 *许可证*  
 实现以下静态函数的选件类:  
  
-   **static BOOL VerifyLicenseKey\( BSTR**  `bstr`\);  
  
-   **static BOOL GetLicenseKey\( DWORD**  `dwReserved` **, BSTR\***  `pBstr`\);  
  
-   **静态 BOOL IsLicenseValid\( \);**  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CComClassFactory2::CreateInstance](../Topic/CComClassFactory2::CreateInstance.md)|创建指定的CLSID的对象。|  
|[CComClassFactory2::CreateInstanceLic](../Topic/CComClassFactory2::CreateInstanceLic.md)|将许可证密钥，创建指定的CLSID的对象。|  
|[CComClassFactory2::GetLicInfo](../Topic/CComClassFactory2::GetLicInfo.md)|检索描述选件类工厂的授权功能信息。|  
|[CComClassFactory2::LockServer](../Topic/CComClassFactory2::LockServer.md)|锁定内存的选件类工厂。|  
|[CComClassFactory2::RequestLicKey](../Topic/CComClassFactory2::RequestLicKey.md)|创建并返回一个许可证密钥。|  
  
## 备注  
 `CComClassFactory2` 实现 [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) 接口，必须是 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)扩展。  **IClassFactory2** 控件对象创建通过许可证。  对一个授权的计算机的选件类工厂可以提供一个运行时许可证密钥。  在完整的许可证的计算机不存在时，此许可证密钥允许应用程序实例化对象。  
  
 ATL对象通过派生通常获取选件类工厂从 [CComCoClass](../../atl/reference/ccomcoclass-class.md)。  此选件类包括宏 [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)，声明 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)，在默认选件类工厂。  若要使用 `CComClassFactory2`，请指定 [DECLARE\_CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md) 宏在对象类定义。  例如：  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/CPP/ccomclassfactory2-class_1.h)]  
  
 **CMyLicense**，对 `CComClassFactory2`的模板参数，必须实现静态函数 `VerifyLicenseKey`、 `GetLicenseKey`和 `IsLicenseValid`。  下面是简单的许可证选件类的示例:  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/CPP/ccomclassfactory2-class_2.h)]  
  
 `CComClassFactory2` 从 **CComClassFactory2Base** 和 *许可证*派生。  **CComClassFactory2Base**，因此，从 **IClassFactory2** 和 **CComObjectRootEx\< CComGlobalsThreadModel \>**派生。  
  
## 继承层次结构  
 `CComObjectRootBase`  
  
 `license`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory2`  
  
 `CComClassFactory2`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComClassFactoryAutoThread Class](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComClassFactorySingleton Class](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)   
 [Class Overview](../../atl/atl-class-overview.md)