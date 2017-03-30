---
---
# <a name="compiler-warning-level-1-c4055"></a>编译器警告（等级 1）C4055  
  
“conversion”：从数据指针“type1”到函数指针“type2”  
  
**已过时︰**不由 Visual Studio 2017 及更高版本生成此警告。

 数据指针被（可能是错误地）强制转换为函数指针。 这是 /Za 下的 1 级警告和 /Ze 下的 4 级警告。  
  
 以下示例生成 C4055：  
  
```C  
// C4055.c  
// compile with: /Za /W1 /c  
typedef int (*PFUNC)();  
int *pi;  
PFUNC f() {  
   return (PFUNC)pi;   // C4055  
}  
```  
  
 在 /Ze 下，这是 4 级警告。  
  
```C  
// C4055b.c  
// compile with: /W4 /c  
typedef int (*PFUNC)();  
int *pi;  
PFUNC f() {  
return (PFUNC)pi;   // C4055  
}  
```