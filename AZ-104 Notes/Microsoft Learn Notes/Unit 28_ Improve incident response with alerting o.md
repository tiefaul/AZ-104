# AZ-104 Notes

## Composition of an Alert Rule

- The composition consists of:
    - Resource:
        - The target. You can assign multiple targets to a single rule.
    - Condition:
        - The *signal type* used to assess the rule. This can be a metric, an activity log, or logs.
    - Actions:
        - Like sending a email, text, using a webhook etc.
        - Can have *action groups*, which typically contain a unique set of recipients for the action
    - Alert Details:
        - An alert name or description that specifies the purpose
        - The severity of the alert:
            - 0: Critical
            - 1: Error
            - 2: Warning
            - 3: Informational
            - 4: Verbose  
                <br/>

## Scope of Alert Rules

- Report on monitoring data using the Azure Monitor pipeline
- in the pipeline you can create rules for these items and more:
    - Metric values
    - Log search queries
    - Activity log events
    - Health of the underlying Azure platform
    - Tests for website availability  
        <br/>

## Manage Alert Rules

- You can enable or disable rules as needed  
    <br/>

## When to use metric alerts

- Note: Metric Alerts are stateful, and Azure Monitor will send a notification only when prerequisite conditions are met.
- Can be used for CPU utilization (EX: notify when cpu usage reaches 90 percent)
- Database storage is getting too low
- Network latency is about to reach unacceptable levels (too high)  
    <br/>

## Composition of a metric alert

- Condition type can be static or dynamic
- Must define the type of statistical analysis to be used with either static or dynamic metric alerts. Examples types are minimum, max, average, and total.  
    <br/>

## Static metric alerts

- You specify the threshold that is used to trigger the alert  
    <br/>

## Dynamic metric alerts

- Use machine-learning tools that Azure provides to automatically improve the accuracy of the thresholds define by the initial rule
- With dynamic, you need to define two more parameters:
    - *Look-back period* - defines how many previous periods need to be evaluated. EX: you set the look-back period to 3, then the assessed data range would be 30 min (three sets of 10 minutes)
    - *Number of violations* - These express how many times the logic condition has to deviate form the expected behavior before the alert rule fires a notification. EX: you set the number of violations to two, the alert would be triggered after two deviations from the calculated threshold  
        <br/>

## Dimensions

- Dimensions enable monitoring of multiple target instances
- Can use to define one metric alert rule and have it applied to multiple related instances.
- Can define the dimensions using the name of each target instance specifically, or use `*`, which is a wildcard that uses all instances