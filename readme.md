# Single Responsibility Principle (S)
### 一個模組應只對唯一的一個角色負責。
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
<a name="OOO"></a>
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
