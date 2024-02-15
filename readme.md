# Single Responsibility Principle(S)
<a name="SingleResponsibilty"></a>

```
class feeCalculator {
    public function calcTax();
    public function calcCreditCardFee();
}
```
若進行修改，將可能同時影響後台與客戶的計算價格。
可以使用interface 進行規範，設立抽象辦法
```
interface FeeCalculator {
    public function calc();
}
class CreditCardFeeHandler implements FeeCalculator {
    public function calc(percentage) {
        return ....;
    }
}
class TaxFeeHandler implements FeeCalculator {
    public function calc(percentage) {
        return ....;
    }
}
```
或使用extends，將預設的方法進行方法複寫(override)
依照上述的辦法，就能夠將客戶與使用者的方法分開。
# Liskov Substitution Principle (L)
<a name="LiskovSubstitution"></a>

```
let sum = 0;
// a,b 必須 >= 0 && <= 50
function add(int a, int b)
{
    result = a + b;
    return result;
}
sum = add(1,5)
```

```
//override 
// a,b 必須 >= 0 && <= 50
function add(int a, int b)
{
    result = a + b;
    // 回傳型態必須為 int
    return result;
}
```