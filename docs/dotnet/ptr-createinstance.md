---
title: ptr::CreateInstance |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- ptr.CreateInstance
- msclr::com::ptr::CreateInstance
- msclr.com.ptr.CreateInstance
- ptr::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- ptr::CreateInstance
ms.assetid: 9e8e4c4c-1651-4839-8829-5857d74470fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8f03a4f0cfb2b231e9a453009155308f7bf407db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112208"
---
# <a name="ptrcreateinstance"></a>ptr::CreateInstance
创建中的 COM 对象的实例`com::ptr`。  
  
## <a name="syntax"></a>语法  
  
```  
void CreateInstance(  
   System::String ^ progid,  
   LPUNKNOWN pouter,  
   DWORD cls_context  
);  
void CreateInstance(  
   System::String ^ progid,  
   LPUNKNOWN pouter  
);  
void CreateInstance(  
   System::String ^ progid  
);  
void CreateInstance(  
   const wchar_t * progid,  
   LPUNKNOWN pouter,  
   DWORD cls_context  
);  
void CreateInstance(  
   const wchar_t * progid,  
   LPUNKNOWN pouter  
);  
void CreateInstance(  
   const wchar_t * progid  
);  
void CreateInstance(  
   REFCLSID rclsid,  
   LPUNKNOWN pouter,  
   DWORD cls_context  
);  
void CreateInstance(  
   REFCLSID rclsid,  
   LPUNKNOWN pouter  
);  
void CreateInstance(  
   REFCLSID rclsid  
);  
```  
  
#### <a name="parameters"></a>参数  
*progid*<br/>
`ProgID` 字符串。  
  
*pouter*<br/>
指向聚合对象的 IUnknown 接口 (控制 IUnknown)。 如果`pouter`未指定，则`NULL`使用。  
  
*cls_context*<br/>
管理新创建的对象的代码将在其中运行的上下文。 值取自`CLSCTX`枚举。 如果`cls_context`未指定，则使用 CLSCTX_ALL 的值。  
  
*rclsid*<br/>
`CLSID` 关联的数据和将用于创建对象的代码。  
  
## <a name="exceptions"></a>异常  
 如果`com::ptr`已拥有对 COM 对象的引用`CreateInstance`引发<xref:System.InvalidOperationException>。  
  
 此函数将调用`CoCreateInstance`，并使用<xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>要转换的任何错误`HRESULT`到相应的异常。  
  
## <a name="remarks"></a>备注  
 `CreateInstance` 使用`CoCreateInstance`创建标识从 ProgID 或 CLSID 的指定对象的新实例。 `com::ptr`引用新创建的对象并将自动释放在析构时所有拥有的引用。  
  
## <a name="example"></a>示例  
 本示例实现使用 `com::ptr` 包装其私有成员 `IXMLDOMDocument` 对象的 CLR 类。 类构造函数使用两种不同形式的`CreateInstance`可以根据 ProgID 或 CLSID 加上 CLSCTX 创建文档对象。  
  
```  
// comptr_createinstance.cpp  
// compile with: /clr /link msxml2.lib  
#include <msxml2.h>  
#include <msclr\com\ptr.h>  
  
#import <msxml3.dll> raw_interfaces_only  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
using namespace msclr;  
  
// a ref class that uses a com::ptr to contain an   
// IXMLDOMDocument object  
ref class XmlDocument {  
public:  
   // construct the internal com::ptr with a null interface  
   // and use CreateInstance to fill it  
   XmlDocument(String^ progid) {  
      m_ptrDoc.CreateInstance(progid);     
   }  
   XmlDocument(REFCLSID clsid, DWORD clsctx) {  
      m_ptrDoc.CreateInstance(clsid, NULL, clsctx);  
   }  
  
   // note that the destructor will call the com::ptr destructor  
   // and automatically release the reference to the COM object  
  
private:  
   com::ptr<IXMLDOMDocument> m_ptrDoc;  
};  
  
// use the ref class to handle an XML DOM Document object  
int main() {  
   try {  
      // create the class from a progid string  
      XmlDocument doc1("Msxml2.DOMDocument.3.0");  
  
      // or from a clsid with specific CLSCTX  
      XmlDocument doc2(CLSID_DOMDocument30, CLSCTX_INPROC_SERVER);  
   }  
   catch (Exception^ e) {  
      Console::WriteLine(e);     
   }  
}  
```  
  
## <a name="requirements"></a>要求  
 **标头文件** \<msclr\com\ptr.h >  
  
 **Namespace** msclr:: com  
  
## <a name="see-also"></a>请参阅  
 [ptr 成员](../dotnet/ptr-members.md)