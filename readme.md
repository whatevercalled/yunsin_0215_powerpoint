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
function add(float a, float b)
{
    result = a + b;
    return result;
}
sum = add(1,5)
```
子型態在覆寫這功能時，先決條件不能比父型態強。若父型態輸入的數字要求是``「大於等於 0 及大於 50」``，子型態輸入的數字則不能是``「大於等於 0 及大於 51」``，但可以是``「大於等於 0 及大於 30」``。
```
//override 
// a,b 必須 >= 0 && <= 50
function add(float a, float b)
{
    result = a + b;
    //加強條件
    // 回傳型態必須為 int
    return result;
}
```
# Interface Segregation Principle (i)
<a name="InterfaceSegregation"></a>

```
interface DailyUsage {
    public function void startEngine();
    public function void move();
}
interface RepairUsage {
    public function void openEngineMode();
    public function void repairWheel();
}
class Car implement DailyUsage, RepairUsage {
    
    public function void openEngineMode() { /*...*/ }

    public function void repairWheel() { /*...*/ }
    public function void startEngine() { /*...*/ }
    
    public function void move() { /*...*/ }
}
class Driver {
    DailyUsage myCar = new Car();
    myCar.startEngine();
    myCar.move();
}
class Mechanic {
    RepairUsage clientCar = new Car();
    clientCar.repairWheel();
    clientCar.openEngineMode();
}
```
雖然上面的功能都引用了car 但是只有 mechanic 可以使用openEngineMode。
運用了interface 進行了方法的隔離。

#  Dependency inversion principle (i)
<a name="Dependencyinversion"></a>

若將mysqlDB=new MongoDB();
將要改寫相當多程式。
step1:避免直接在建構子中，直接初始化Mysql，而是將其在外部初始化，再進行傳參。
初始:
```
class Controller {
    
    Mysql mysqlDB = new Mysql();
    string dbHost = mysqlDB.host;
}
```
注入依賴後:
```
class Controller {
    private Mysql mysqlDB;
    public Controller(Mysql mysqlDB)
    {
        this.mysqlDB = mysqlDB;
    }
    string dbHost = this.mysqlDB.host;
}
```
建立interface，介面隔離Mysql與MangoDB。進一步降低耦合。
```
class Controller {
    private Database database;
    public Controller(Database database) //只注入 Database 介面
    {
        this.database = database;
    }
    string dbHost = this.database.gethost();
}
interface Database {
    public string getHost();
    public string getPort();
    public string getUsername();
    public string getPassword();
}
class Mysql implement Database {
    public string getHost() {
        ...
        return host;
    }
    ...
}
class MangoDb implement Database {
    public string getHost() {
        ...
        return host;
    }
    ...
}
```