# Executing Rules

## A Simple Processor Request

The simplest type request that can be sent to the processor follows the structure below \(there are other more complex types of requests\). It must at the very least contain an “inputs” and “outputs” node.

```text
{
    "inputs": [
        {
            "_class": "driver",
            "gender": "MALE",
            "licenseYears": 2,
            "age": 23
        },
        {
            "_class": "extras",
            "extraCar": true
        }
    ],
    "outputs": [
        "policy"
    ]
}
```

### Request Inputs

An “input” is the data you are sending to the processor. 

If it has a “\_class” property then it relates directly to a type you defined in the ruleset and benefits from compile time checks. If it does not have the “\_class” property then the data is treated as a raw Map of key/value pairs. 

Any properties defined in the input are mapped either to the type or treated as a key. You can use these as the properties in your rules. 

An input can contain any number of non-unique elements. 

They can be as simple as you like \(we prefer single-level facts because it is easier to work with in the rules\) or as complicated and deep as you like.

If you want to send over multiple items of the same element, somewhat like a batch, you can do that too and, depending on the ruleset, multiple “outputs” can be returned or the result can be aggregated into a single response.

### Request Outputs

Outputs allows you to filter what types of facts are returned in the results. They can also include your inputs if you want those to be returned back with the results.

This feature is a way to control/limit that what comes back in the results is only what you are interested in. This can be useful when a ruleset returns a variety of related results but you only want to see a specific selection or subset for your purposes.

For example, if we remove the “driver” from the outputs then only the “policy” fact will come back. When we have both the “driver” and “policy,” even though “driver” really is an input, it and the resulting “policy” fact will be returned.

