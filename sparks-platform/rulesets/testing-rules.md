# Testing Rules

One of the best features of the Sparks Platform Rule Services is the ability to immediately test one or more rulesets with sample \(or real\) inputs. The rule tester speeds up the process and gives designers a quick way to validate, check, and test the rulesets that are exposed.  


{% hint style="warning" %}
You must have the appropriate container\(s\) running before using the rule tester. Unlike the designer/debugger which dynamically creates the container the tester runs against running containers only.
{% endhint %}

## Launching the Ruleset Tester

To open the ruleset tester, click on the Test Rules button in the ruleset.

![](https://lh5.googleusercontent.com/MsTI5ZhIO4C5JnnGbGRlOLs-HZaGjLko_yzOBADgdyb9XdBWgFR_foQAGAARp0mRSyKFnIsrwLP7maESIyV77hugRZAlYfuC4bHpWwMMFMkqo-P4cf_vy_AaPDsebT6r2-wb6nPj)

This will open a screen like below:

![](https://lh4.googleusercontent.com/YBkS6xYdnRGhsZMadzF8dOglx7kNDkhwFvS-R2okg97ry2X8LiGOy7TF6FVnZqhHO2UQyrfAfQLQSqfeMWsFFdFHf5CtFphelQuhKrjE5Kc98lUtOePfUGMNMqUnF774X5tHaq7X)

By default, all running containers for the ruleset will be selected as targets in the container selection drop-down in the upper-right-hand corner.

If only one container is started or you want to specify which containers to test against, click the drop-down and select the containers you want.

![](https://lh4.googleusercontent.com/MCYJ2mRxm2oPsMYxhWTgZuxLHsknnR1ZCKw_clrOapS71MWWEp4ADgOqgDoCC-kaLwQfIoRVVhpIaI8idOHxHt9YVPoMmr53pE__aEi8Welkw4VzTw-Ua4HPAxIKuHsn5PIwOdXr)

For our example, we have started both the Approve or Deny Policy and Calculate Policy Price ruleset containers.

If a ruleset contains an “example” as a part of its definition \(managed in the Ruleset screen\), you can select that example input from the Input dropdown on the left-hand-side.

![](https://lh5.googleusercontent.com/AWgxus-qNvB1uOKNm79zi1an3Bmx5ArsATFN0Ln9zmgOp3Dq2z-uAeK5erzuw-lwpvRMnbu3tzCx08UTFbn9hE_EG4QmuQ8T6gzKbT1O2X_9QxRm5YDGeH9fTUXlNhOeHKPwkUzA)

Example inputs, when available, are a good way to provide a template-like starting point for users to work with. The example can be modified in the tester and it only persists for that session. Other users who select the example will get the original template and they can make their own changes.

When testing rules they will always expect some “input” in a standardized structure \(you can define the expectations within the inputs but for simple requests they will always have an inputs and outputs node\) and produce some “output.”

The structure of the simple “input/output” payload used for testing is described in detail at [Anatomy of a Processor Request](rulesets-api/executing-rules.md#a-simple-processor-request).

{% page-ref page="rulesets-api/executing-rules.md" %}



## Running a Test

1. Select the container\(s\) you want to test against.
2. Select an example input to start with and modify as needed, copy-and-past one in, or create an input from scratch.
3. Click the Run button in the upper right-hand corner to execute the test.

The results of the execution will be shown in the output window when it completes.

### Testing Multiple Rulesets

If more than one container is selected, the input will be processed against each of the rulesets and you can see how an input may be handled by multiple, maybe different, rulesets.

![](https://lh4.googleusercontent.com/kYmNbJY3yM3xuMNyP9WC-IRbL5QvhfOtAWmcyS3jvIWhoepBeTDXmjcw8_rouGiZ2CD3tnxB_k7fzLp9Q4pcw5a5BoUsm3bTUvqY9S55LlDtBwEp3KxP8gAcPurcGtMOMhTAEwPB)

This is a unique feature in the Sparks Platform to be able to pass in a “real-world” input and see how different rulesets may evaluate the same data. You can also merge the expected inputs from two different rulesets into one and see if they both fire correctly. Another good use of this feature is if different versions of the same ruleset are running and you want to compare the results.

## Examples

Below are some example scenarios you can experiment with using the “insurance” example to see how the rules work. To follow along, create a new project using the Insurance template. It is probably a good idea to browse tough the rules of this project before-hand and get a general idea of the logic that has been setup.

Once you are comfortable with the rules, try to change values, remove properties, or even whole sections and see the rules react to those changes.

The structure of the “input” payload is described in more detail at [Anatomy of a Processor Request](rulesets-api/executing-rules.md#a-simple-processor-request) later in this document.

### Approve or Reject a Policy

We want to see how the Approve or Deny Policy reacts when a driver is underage. In this case, the rules should reject the policy.

Before beginning, make sure only the Approve or Deny Policy container is selected and select the Approve or Deny Policy Example in the Input drop-down.

* Change the age to 17. Result, the policy is REJECTED
* Change the age to 25. Result, the policy is APPROVED

### Calculate a Policy Price

In this scenario we want to see how the policy price changes based on different parameters. For this example, make sure the Calculate Policy Price is the only container we are testing against \(disable any others in the drop-down if needed\).

Before beginning, make sure only the Calculate Policy Price container is selected and select the Calculate Policy Price Example in the Input drop-down.

* Change the `alarmSystemValue`. Result, the insurancePrice changes
* Change the `age` to 17. Result, the policy is rejected and no `insurancePrice` is given
* Remove the whole \`details\` block. Result, the policy is cheaper because the car is not on the street

