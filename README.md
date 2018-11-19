# GoF_DesignPattern_Examples
Examples for design pattern

## 1. Factory
### Before
```Java
public Money calculatePay(Employee e) throws InvalidEmployeeType {
 switch (e.type) {
  case COMMISSIONED:
   return calculateCommissionedPay(e);
  case HOURLY:
   return calculateHourlyPay(e);
  case SALARIED:
   return calculateSalariedPay(e);
  default:
   throw new InvalidEmployeeType(e.type);
 }
}

### After
public abstract class Employee {
 public abstract public abstract public abstract
 boolean isPayday();
 Money calculatePay();
 void deliverPay(Money pay);
}
-- -- -- -- -- -- -- -- -
public interface EmployeeFactory {
 public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType;
}
-- -- -- -- -- -- -- -- -
public class EmployeeFactoryImpl implements EmployeeFactory {
 public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType {
  switch (r.type) {
   case COMMISSIONED:
    return new CommissionedEmployee(r);
   case HOURLY:
    return new HourlyEmployee(r);
   case SALARIED:
    return new SalariedEmploye(r);
   default:
    throw new InvalidEmployeeType(r.type);
  }
 }
}
```
