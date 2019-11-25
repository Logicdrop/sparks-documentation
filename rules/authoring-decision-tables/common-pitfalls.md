# Common Pitfalls



The following are some common issues that users may face when creating/modifying the Decision Table, and processing rules based off it and the solutions to these issues:

### 1. Formula in rule cell not working

When entering formulas in rule cells that act on previously set properties of models, users may find that the computation isn’t working. A common misstep is to write the formula like this:

```text
fee.getBaseFee() - fee.getDiscount()
```

When, for example the base fee, column has been defined like this:

![](../../.gitbook/assets/5.png)

When declaring a model, and not assigning a variable name, the default name to access the model in formulas is to add “Fact” to the end of the model name. Therefore, `fee.getBaseFee()` should be `feeFact.getBaseFee`. The reason for this appended word is for the rule processor to use terminology pertaining to rules.

### **2. Merge header not being used**

Users sometimes copy the same value in multiple rows in the same column. To save time, the MERGE header should be set to TRUE for that column so that copying multiple times is not necessary.

### **3. String comparison not working**

Another common pitfall, is that users may find that string comparisons aren’t properly functioning. A common reason is forgetting to include modifiers such as lc \(lower case\) or uc\(upper case\).

### **4. Property not updating**

The Logicdrop Ru

